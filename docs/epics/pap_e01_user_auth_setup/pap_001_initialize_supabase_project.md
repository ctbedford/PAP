# PAP-1: Initialize Supabase Project and Configure Basic Auth Settings (Email/Password)

*Epic: [PAP-E01 - User Authentication & Basic Account Setup (MVP)](../pap_epic_001_user_auth_setup.md)*

---

## Overview
This document provides refined, up-to-date, and comprehensive guidance for initializing a Supabase project and configuring secure email/password authentication for the PAP Web App MVP, reflecting best practices as of May 2025.

---

## Step-by-Step Instructions

### 1. Create a Supabase Account and Project
- Go to [supabase.com](https://supabase.com).
- Sign up or log in.
- In your organization's dashboard, click **New Project**.
    - **Organization:** Select or create one.
    - **Project Name:** Use something descriptive (e.g., "PAP-WebApp-MVP").
    - **Database Password:** Generate a strong, unique password. Store it securely (e.g., password manager).
    - **Region:** Select the closest region to your main user base.
    - **Pricing Plan:** Choose the Free tier for MVP (sufficient resources for development/testing).
- Click **Create project** and wait for provisioning.

### 2. Secure and Store Your Project API Keys
- In your project dashboard, go to **Project Settings** → **API**.
- Note the following:
    - **Project URL:** e.g., `https://<your-project-ref>.supabase.co`
    - **API Keys:**
        - **anon (publishable) key:** Safe for client-side use (subject to RLS). Will be renamed to "publishable" key in future Supabase updates.
        - **service_role (secret) key:** Full admin access, bypasses RLS. **Never expose in client code or commit to git.** Will be renamed to "secret" key.
- **Action:** Copy the Project URL and anon key. Store as environment variables for your Next.js app (covered in PAP-2).

### 3. Configure Authentication Settings in Supabase Dashboard
- Go to **Authentication** (shield icon).
- **Providers:**
    - **Email:** Ensure enabled (default). Other providers (Google, GitHub, etc.) should be disabled for MVP.
- **Settings/Configuration:**
    - **Site URL:** Set to your main deployment URL (e.g., `http://localhost:3000` for dev, later your Vercel prod URL).
    - **Additional Redirect URLs:** Add any others needed (e.g., specific localhost/prod paths). Be specific for security.
    - **Enable "Confirm email":**
        - For solo MVP, you *can* disable for faster testing (accounts active immediately).
        - For production/multi-user, **enable** to require email verification.
    - **Enable "Secure email change":** Keep enabled (default).
    - **Enable manual sign up/sign in:** Ensure both are enabled (default).
- **Password Policy:**
    - Set minimum length (consider 10–12 chars for extra security).
    - Configure required character types as desired.
    - Ensure "Prevent use of leaked passwords" is enabled.
- **Email Templates:**
    - Defaults are functional for MVP. Customize later if needed.
    - For "Confirm Email", ensure the link uses `{{ .ConfirmationURL }}` or is constructed per Supabase docs.
- **SMTP Settings:**
    - Supabase's built-in sender is fine for testing, but has low limits.
    - For reliable delivery (esp. in production), configure a custom SMTP provider (SendGrid, Brevo, AWS SES, etc.).

### 4. Review Default Auth Schema (Optional)
- In the dashboard, see the `auth.users` and related tables in Table Editor.
- You usually don't modify these directly, but it's good to be aware of their structure.
- For user-specific non-auth data, you'll typically create a public `profiles` table linked to `auth.users.id`.

---

## Best Practices & Notes (as of May 2025)
- **Never expose your service_role/secret key in frontend code or commit it to version control.**
- Store your Project URL and anon (publishable) key as environment variables in `.env.local` for Next.js.
- For MVP/solo use, you can disable email confirmation to streamline dev. For production, always enable it.
- Familiarize yourself with Supabase's evolving terminology (anon→publishable, service_role→secret).
- If you plan to use auth emails (confirmation, password reset) in production, set up a custom SMTP provider.

---

## References
- [Supabase Docs: Getting Started](https://supabase.com/docs/guides/getting-started)
- [Supabase Docs: Auth](https://supabase.com/docs/guides/auth)
- [Supabase Docs: Managing API Keys](https://supabase.com/docs/guides/api/keys)
- [Supabase Docs: Email Auth](https://supabase.com/docs/guides/auth/auth-email)
- [Supabase Docs: SMTP Setup](https://supabase.com/docs/guides/auth/auth-smtp)

---

*This guidance is current as of May 2025 and is tailored for the PAP Web App MVP context. For future updates, always check the official Supabase documentation.*
