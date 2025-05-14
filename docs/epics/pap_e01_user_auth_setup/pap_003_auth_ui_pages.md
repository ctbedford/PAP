# PAP-3: Create Next.js Pages/Components for Sign Up, Login, and Profile Display

*Epic: [PAP-E01 - User Authentication & Basic Account Setup (MVP)](../pap_epic_001_user_auth_setup.md)*

---

## Overview
This document provides refined, up-to-date, and comprehensive guidance for building the UI for authentication (Sign Up, Login) and Profile display in a Next.js App Router project, using Shadcn/ui and Tailwind CSS. The focus is on structure and best practices as of May 2025, preparing for robust logic in later tasks.

---

## Step-by-Step Instructions

### 1. Initialize Shadcn/ui and Add Components
- Initialize Shadcn/ui (if not done):
  ```bash
  npx shadcn-ui@latest init
  ```
- Add required components:
  ```bash
  npx shadcn-ui@latest add card button input label
  ```
- Components will be added to `components/ui/`.

### 2. Page Structure (Next.js App Router)
- **Sign Up Page:** `app/auth/signup/page.tsx`
- **Login Page:** `app/auth/login/page.tsx`
- **Profile Page:** `app/profile/page.tsx`
- Each page exports a React component.

### 3. Build UI Components (Client Components)
- All pages should include `'use client'` at the top for interactivity.
- Use Shadcn/ui components (`Card`, `Input`, `Button`, `Label`) for form structure and Tailwind CSS for layout.

#### Example: app/auth/signup/page.tsx
```tsx
'use client'
import { useState } from 'react'
import { Button } from '@/components/ui/button'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from '@/components/ui/card'
import Link from 'next/link'

export default function SignUpPage() {
  const [email, setEmail] = useState('')
  const [password, setPassword] = useState('')
  const [confirmPassword, setConfirmPassword] = useState('')

  const handleSignUp = async (event: React.FormEvent<HTMLFormElement>) => {
    event.preventDefault()
    // Logic for Supabase signup will be added in PAP-4
    if (password !== confirmPassword) {
      // Handle password mismatch
      return
    }
  }

  return (
    <div className="flex justify-center items-center min-h-screen bg-background">
      <Card className="w-full max-w-md">
        <CardHeader>
          <CardTitle className="text-2xl">Create your PAP Account</CardTitle>
          <CardDescription>Enter your details to get started.</CardDescription>
        </CardHeader>
        <CardContent>
          <form onSubmit={handleSignUp}>
            <div className="grid gap-4">
              <div className="grid gap-2">
                <Label htmlFor="email">Email</Label>
                <Input id="email" type="email" value={email} onChange={(e) => setEmail(e.target.value)} required />
              </div>
              <div className="grid gap-2">
                <Label htmlFor="password">Password</Label>
                <Input id="password" type="password" value={password} onChange={(e) => setPassword(e.target.value)} required />
              </div>
              <div className="grid gap-2">
                <Label htmlFor="confirmPassword">Confirm Password</Label>
                <Input id="confirmPassword" type="password" value={confirmPassword} onChange={(e) => setConfirmPassword(e.target.value)} required />
              </div>
              <Button type="submit" className="w-full">Sign Up</Button>
            </div>
          </form>
        </CardContent>
        <CardFooter className="text-center text-sm">
          <p>
            Already have an account?{' '}
            <Link href="/auth/login" className="underline">Log In</Link>
          </p>
        </CardFooter>
      </Card>
    </div>
  )
}
```

#### Example: app/auth/login/page.tsx
- Similar to Sign Up, but only email and password fields. Add links to Sign Up and Forgot Password.

#### Example: app/profile/page.tsx
```tsx
'use client'
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'

export default function ProfilePage() {
  const userEmailPlaceholder = 'Loading your email...'

  const handleLogout = async () => {
    // Logout logic will be implemented in PAP-5
  }

  return (
    <div className="container mx-auto py-10 flex justify-center">
      <Card className="w-full max-w-md">
        <CardHeader>
          <CardTitle className="text-2xl">Your Profile</CardTitle>
          <CardDescription>Welcome to your Principled Actualization Protocol dashboard.</CardDescription>
        </CardHeader>
        <CardContent className="grid gap-4">
          <div>
            <p className="text-sm font-medium">Email</p>
            <p className="text-muted-foreground">{userEmailPlaceholder}</p>
          </div>
        </CardContent>
        <CardFooter>
          <Button onClick={handleLogout} variant="outline" className="w-full">Log Out</Button>
        </CardFooter>
      </Card>
    </div>
  )
}
```

### 4. Global Layout
- Ensure `app/layout.tsx` imports `globals.css` and sets up Tailwind and Shadcn/ui theme variables.
- Add a simple Navbar in the layout for navigation as needed (optional for MVP).

---

## Best Practices & Notes (as of May 2025)
- Use App Router conventions: `page.tsx` in nested route directories.
- Client Components for all interactive/auth pages.
- Use Shadcn/ui CLI to add components for local customization.
- Use Tailwind utility classes for layout and spacing.
- Actual form logic (Supabase calls, validation, session) will be added in PAP-4 and PAP-5.

---

## References
- [Shadcn/ui Docs](https://ui.shadcn.com/docs)
- [Next.js App Router Docs](https://nextjs.org/docs/app/building-your-application/routing)
- [Supabase Auth UI Patterns](https://supabase.com/docs/guides/auth/auth-helpers/nextjs)

---

*This guidance is current as of May 2025 and is tailored for the PAP Web App MVP context. For future updates, always check the official documentation.*
