# PAP-2: Set up Supabase Client in Next.js Application

*Epic: [PAP-E01 - User Authentication & Basic Account Setup (MVP)](../pap_epic_001_user_auth_setup.md)*

---

## Overview
This document provides refined, up-to-date, and comprehensive guidance for integrating Supabase into a Next.js (App Router) application, reflecting best practices as of May 2025. The approach emphasizes the use of `@supabase/ssr` for correct session management across all Next.js rendering environments (Client Components, Server Components, Route Handlers, Server Actions).

---

## Step-by-Step Instructions

### 1. Install Supabase JS Libraries
In your Next.js project root, run one of the following:

```bash
npm install @supabase/supabase-js @supabase/ssr
# or
yarn add @supabase/supabase-js @supabase/ssr
# or
pnpm add @supabase/supabase-js @supabase/ssr
# or
bun add @supabase/supabase-js @supabase/ssr
```
- `@supabase/supabase-js` is the core JavaScript client.
- `@supabase/ssr` provides helper functions for SSR frameworks like Next.js to manage auth state (cookies) correctly.

### 2. Set Up Environment Variables
- Create a `.env.local` file in your project root (add it to `.gitignore`).
- Add your Supabase Project URL and anon key:

```dotenv
NEXT_PUBLIC_SUPABASE_URL=https://<your-project-ref>.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=<your-anon-key>
```
- The `NEXT_PUBLIC_` prefix makes these accessible in the browser.
- For any server-only secret (like the service_role key), omit the prefix and do not expose in client code.

### 3. Create Supabase Client Utility Functions (Using @supabase/ssr)
Centralize client creation in a `utils/supabase` or `lib/supabase` directory within your `app` or `src` folder.

#### utils/supabase/client.ts (for Client Components)
```typescript
// utils/supabase/client.ts
import { createBrowserClient } from '@supabase/ssr'
import type { Database } from '@/types/supabase' // Generate types (see below)

export function createSupabaseBrowserClient() {
  return createBrowserClient<Database>(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!
  )
}
```
This client is for browser-side operations. Cookie management is handled by middleware and server-side clients.

#### utils/supabase/server.ts (for Server Components, Route Handlers, Server Actions)
```typescript
// utils/supabase/server.ts
import { createServerClient, type CookieOptions } from '@supabase/ssr'
import { cookies } from 'next/headers'
import type { Database } from '@/types/supabase'

export function createSupabaseServerClientReadOnly() {
  const cookieStore = cookies()
  return createServerClient<Database>(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
    {
      cookies: {
        get(name: string) {
          return cookieStore.get(name)?.value
        },
        // No set/remove for read-only client
      },
    }
  )
}

export function createSupabaseServerClient() {
  const cookieStore = cookies()
  return createServerClient<Database>(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
    {
      cookies: {
        get(name: string) {
          return cookieStore.get(name)?.value
        },
        set(name: string, value: string, options: CookieOptions) {
          try {
            cookieStore.set(name, value, options)
          } catch (error) {
            // In Server Components, `set` and `remove` throw an error
          }
        },
        remove(name: string, options: CookieOptions) {
          try {
            cookieStore.delete(name, options)
          } catch (error) {
            // In Server Components, `set` and `remove` throw an error
          }
        },
      },
    }
  )
}
```
- Use `createSupabaseServerClientReadOnly` for data fetching in Server Components.
- Use `createSupabaseServerClient` for mutations in Server Actions or Route Handlers.

### 4. Configure middleware.ts for Session Management
Place this at your project root or in `src/`:
```typescript
// middleware.ts
import { createServerClient, type CookieOptions } from '@supabase/ssr'
import { NextResponse, type NextRequest } from 'next/server'

export async function middleware(request: NextRequest) {
  let response = NextResponse.next({
    request: {
      headers: request.headers,
    },
  })

  const supabase = createServerClient(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
    {
      cookies: {
        get(name: string) {
          return request.cookies.get(name)?.value
        },
        set(name: string, value: string, options: CookieOptions) {
          request.cookies.set({ name, value, ...options })
          response = NextResponse.next({
            request: {
              headers: request.headers,
            },
          })
          response.cookies.set({ name, value, ...options })
        },
        remove(name: string, options: CookieOptions) {
          request.cookies.set({ name, value: '', ...options })
          response = NextResponse.next({
            request: {
              headers: request.headers,
            },
          })
          response.cookies.set({ name, value: '', ...options })
        },
      },
    }
  )

  // Refresh session if expired
  await supabase.auth.getUser()

  return response
}

export const config = {
  matcher: [
    '/((?!_next/static|_next/image|favicon.ico|.*\\.(?:svg|png|jpg|jpeg|gif|webp)$).*)',
  ],
}
```
- This ensures session cookies are refreshed and auth state is available to Server Components and Route Handlers.
- Adjust the matcher as needed to avoid static assets.

### 5. Generate TypeScript Types for Database
- Install Supabase CLI: `npm install supabase --save-dev`
- Log in: `npx supabase login`
- Link your project: `npx supabase link --project-ref <your-project-ref>`
- Generate types:

```bash
npx supabase gen types typescript --linked > types/supabase.ts
```
- Reference the generated `Database` type in your client/server utility files for full type safety.

---

## Best Practices & Notes (as of May 2025)
- Use `@supabase/ssr` for all Next.js App Router projects.
- Separate client/server utilities for Supabase is a clean and scalable pattern.
- All mutations (login, signup, logout, writes) should be handled in Server Actions or Route Handlers using the server client, not directly in Client Components.
- Use middleware to ensure session cookies are always up to date for SSR.
- Never expose your service_role/secret key in frontend code or commit it to version control.

---

## References
- [Supabase Docs: Next.js SSR Guide](https://supabase.com/docs/guides/auth/server-side/nextjs)
- [Supabase Docs: @supabase/ssr](https://supabase.com/docs/reference/javascript/ssr)
- [Supabase Docs: Generating Types](https://supabase.com/docs/guides/database/typescript)

---

*This guidance is current as of May 2025 and is tailored for the PAP Web App MVP context. For future updates, always check the official Supabase documentation.*
