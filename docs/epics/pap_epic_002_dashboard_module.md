**Epic Name:** EPIC: PAP-E02 - Dashboard Module (MVP)

**1. Epic Summary / Goal:**
   * To develop a central Dashboard for the PAP Web App that provides the user with an at-a-glance overview of their current priorities, key information, and quick access to essential features, enhancing productivity and focus.

**2. Business Value / User Benefit (The "Why"):**
   * Offers immediate visibility into the user's PAP landscape (e.g., current Rocks, today's tasks), reducing cognitive load and aiding in daily planning.
   * Serves as a primary navigation hub, improving user experience and efficiency.
   * Reinforces engagement with the PAP by surfacing timely reminders and relevant data.

**3. Scope:**
   * **In Scope (Key Deliverables/Features):**
        * Design of a simple Dashboard UI layout (Shadcn/ui + Tailwind).
        * Creation of a Next.js page for the Dashboard (e.g., `/dashboard`).
        * Data fetching (client-side or server-side) for:
            * Current 90-Day Rocks (titles, basic status) from Supabase.
            * Tasks due "today" or high-priority tasks from Supabase.
        * Development of React components (Shadcn/ui) to display the fetched information.
        * Quick link/button to initiate a "New Phenomenological Log Entry."
        * Display a reminder for the next (conceptual) "L10 Alignment Meeting" (static or simple date logic for MVP).
   * **Out of Scope (For this Epic/MVP Release):**
        * Advanced dashboard customization or personalization by the user.
        * Complex data visualizations or charts.
        * Real-time data updates (polling or WebSockets).
        * Integration with external calendars or to-do lists.
        * Detailed historical data or trend analysis on the dashboard.

**4. Key Features / User Stories (Derived from original PAP tasks PAP-8 to PAP-12):**
   * `PAP-STORY-009`: As a user, I want to see a clear and organized dashboard layout when I log in so that I can quickly understand my current status and priorities.
     * (Derived from PAP-8)
   * `PAP-STORY-010`: As a user, I want my dashboard to display a list of my current 90-Day Rocks (titles and status) so that I can stay focused on my quarterly objectives.
     * (Derived from PAP-10, PAP-11)
   * `PAP-STORY-011`: As a user, I want my dashboard to show tasks that are due today (or high priority) so that I can manage my daily workload effectively.
     * (Derived from PAP-10, PAP-11)
   * `PAP-STORY-012`: As a user, I want a quick way to add a new Phenomenological Log entry directly from my dashboard so that I can easily capture insights as they arise.
     * (Derived from PAP-12)
   * `PAP-STORY-013`: As a user, I want to see a reminder for my next "L10 Alignment Meeting" on my dashboard so that I can prepare for my weekly review.
     * (Derived from PAP-10, PAP-11) 
   * `PAP-STORY-014`: As a developer, I need a dedicated Next.js page (e.g., `/dashboard`) to serve as the main entry point for the dashboard view.
     * (Derived from PAP-9)

**5. Acceptance Criteria (High-Level for Epic):**
   * The dashboard page loads correctly after user login.
   * Displays current Rocks (titles/status) fetched from Supabase.
   * Displays tasks due "today" (or priority tasks) fetched from Supabase.
   * Provides a functional quick link/button to navigate to the new log entry page/modal.
   * Shows a placeholder or simple logic-based reminder for the L10 meeting.
   * UI is clean, readable, and usable on desktop browsers.

**6. Dependencies:**
   * `EPIC: PAP-E01 - User Authentication & Basic Account Setup (MVP)` must be completed (user needs to be logged in).
   * Initial schema and data for Rocks and Tasks (from `EPIC: PAP-E04` and `EPIC: PAP-E05`) must be available in Supabase for fetching, or placeholder data used if developed in parallel.
   * Schema for Phenomenological Log (from `EPIC: PAP-E06`) for the quick link target.

**7. Metrics for Success (Optional for Epic, but good for focus):**
   * User (self) finds the dashboard informative and uses it as the primary landing page.
   * Key information (Rocks, Tasks) is accurately displayed.

**8. Notes / Assumptions:**
   * Data fetching strategy (client-side SWR/React Query vs. Next.js server-side props) will be determined during implementation based on simplicity and MVP needs.
   * "Today's Tasks" logic might be simplified for MVP (e.g., tasks with a due date of today, or a manually flagged priority task).
   * The L10 Meeting reminder will likely be a static text or very simple date calculation for MVP, not a full calendar integration.
