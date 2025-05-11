**Epic Name:** EPIC: PAP-E04 - "PAP Cycles & Rocks" Module (MVP)

**1. Epic Summary / Goal:**
   * To enable users to define 90-day "PAP Cycles" (quarters) and manage their high-priority objectives ("Rocks") for each cycle. This module facilitates focused effort on key goals within a defined timeframe.

**2. Business Value / User Benefit (The "Why"):**
   * Implements a core component of the PAP methodology: time-boxed, high-impact goal setting (Quarterly Rocks).
   * Helps users break down their longer-term Painted Picture into actionable 90-day segments.
   * Provides a clear structure for prioritizing work and tracking progress on the most important objectives.

**3. Scope:**
   * **In Scope (Key Deliverables/Features):**
        * Definition of Supabase table schemas for `Cycles` (e.g., user_id, start_date, end_date, theme/focus) and `Rocks` (e.g., cycle_id, user_id, title, objective_description, S.M.A.R.T. criteria, status).
        * Next.js pages for managing Cycles (e.g., view list, create new) and for viewing/editing Rocks within a specific Cycle.
        * Forms (using React Hook Form) for creating and editing Cycles and Rocks, with data persisted to Supabase.
        * UI components (using Shadcn/ui) to list Cycles and Rocks.
        * Functionality to update the status of a Rock (e.g., To Do, In Progress, Done).
   * **Out of Scope (For this Epic/MVP Release):**
        * Automated calculation of Rock completion percentages.
        * Linking Rocks to specific Painted Picture dimensions directly in the UI (conceptual link only for MVP).
        * Complex filtering or sorting of Rocks beyond basic status or cycle.
        * Archiving or historical analysis of past cycles/rocks beyond simple listing.
        * Visual progress bars or detailed analytics for Rocks.

**4. Key Features / User Stories (Derived from original PAP tasks PAP-18 to PAP-21):**
   * `PAP-STORY-020`: As a user, I want to define the database structure (Supabase tables) for `PAP Cycles` (with start/end dates, theme) and `Rocks` (with title, objective, SMART criteria, status, linked to a cycle) so that I can store and manage my quarterly planning.
     * (Derived from PAP-18)
   * `PAP-STORY-021`: As a user, I want dedicated pages in the app to create new PAP Cycles and to view a list of my cycles, so I can manage my 90-day planning periods.
     * (Derived from PAP-19)
   * `PAP-STORY-022`: As a user, for each PAP Cycle, I want to be able to view, add, edit, and delete my Quarterly Rocks, so I can define and refine my key objectives for that period.
     * (Derived from PAP-19, PAP-20)
   * `PAP-STORY-023`: As a user, I want to be able to update the status of my Rocks (e.g., To Do, In Progress, Done), so I can track my progress throughout the cycle.
     * (Derived from PAP-21)
   * `PAP-STORY-024`: As a developer, I need to implement forms for creating and editing Cycle and Rock details, ensuring data is correctly saved to Supabase.
     * (Derived from PAP-20)

**5. Acceptance Criteria (High-Level for Epic):**
   * User can create a new 90-day PAP Cycle with a start date, end date, and theme.
   * User can add multiple Rocks to a Cycle, each with a title, objective, and S.M.A.R.T. criteria.
   * User can view a list of their Cycles and the Rocks associated with each Cycle.
   * User can update the status of a Rock.
   * All data related to Cycles and Rocks is persisted correctly in Supabase.

**6. Dependencies:**
   * `EPIC: PAP-E01 - User Authentication & Basic Account Setup (MVP)` must be completed.
   * Supabase project and client fully configured.

**7. Metrics for Success (Optional for Epic, but good for focus):**
   * User (self) can successfully define at least one PAP Cycle and populate it with several Rocks.
   * User (self) updates Rock statuses throughout a conceptual 90-day period.

**8. Notes / Assumptions:**
   * A "Rock" is a high-priority quarterly goal, typically 3-5 per cycle.
   * S.M.A.R.T. criteria (Specific, Measurable, Achievable, Relevant, Time-bound) will likely be a text field for the user to fill in for MVP, rather than individual structured fields.
   * Rock status will be a simple selection (e.g., dropdown or radio buttons) for MVP.
