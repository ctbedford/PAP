**Epic Name:** EPIC: PAP-E05 - "Embodied Actions & Tasks" Module (MVP)

**1. Epic Summary / Goal:**
   * To enable users to break down their Quarterly Rocks into smaller, actionable tasks and track the status of these tasks. This module bridges the gap between high-level objectives (Rocks) and daily execution.

**2. Business Value / User Benefit (The "Why"):**
   * Facilitates the practical execution of Quarterly Rocks by detailing the specific actions required.
   * Provides clarity on what needs to be done on a more granular level, improving focus and reducing overwhelm.
   * Allows users to monitor progress towards their Rocks by tracking the completion of associated tasks.

**3. Scope:**
   * **In Scope (Key Deliverables/Features):**
        * Definition of a Supabase table schema for `Tasks` (e.g., rock_id, user_id, description, status, optional due_date).
        * UI functionality integrated within the Rock detail view (from `EPIC: PAP-E04`) to add, view, and edit Tasks linked to that specific Rock.
        * Use of Shadcn/ui components for task list display and input forms (using React Hook Form).
        * Simple status updates for tasks (e.g., To Do, Done).
   * **Out of Scope (For this Epic/MVP Release):**
        * Sub-tasks or nested tasks.
        * Time tracking or effort estimation for tasks.
        * Assigning tasks to other users (MVP is single-user focused).
        * Task dependencies or Gantt chart views.
        * Recurring tasks.
        * Notifications or reminders for task due dates (beyond what might appear on the dashboard).

**4. Key Features / User Stories (Derived from original PAP tasks PAP-22 to PAP-25):**
   * `PAP-STORY-025`: As a user, I want to define the database structure (Supabase table) for `Tasks`, including fields for a description, status, an optional due date, and a clear link to its parent Rock, so I can organize the work needed for my objectives.
     * (Derived from PAP-22)
   * `PAP-STORY-026`: As a user, when viewing the details of a specific Rock, I want to be able to add new tasks, view existing tasks, and edit their details (description, due date), so I can manage the work associated with that Rock.
     * (Derived from PAP-23)
   * `PAP-STORY-027`: As a user, I want to be able to update the status of a task (e.g., "To Do", "Done"), so I can track its completion and see progress towards my Rock.
     * (Derived from PAP-23, PAP-25)
   * `PAP-STORY-028`: As a developer, I need to use consistent UI components (Shadcn/ui) and forms (React Hook Form) for managing tasks to ensure a good user experience and maintainable code.
     * (Derived from PAP-24)

**5. Acceptance Criteria (High-Level for Epic):**
   * User can add one or more tasks to an existing Rock, providing a description and optionally a due date.
   * Tasks associated with a Rock are displayed clearly when viewing that Rock.
   * User can edit the description and due date of an existing task.
   * User can update the status of a task (e.g., mark it as "Done").
   * Task data is correctly persisted in Supabase and linked to the correct Rock and user.

**6. Dependencies:**
   * `EPIC: PAP-E01 - User Authentication & Basic Account Setup (MVP)` must be completed.
   * `EPIC: PAP-E04 - "PAP Cycles & Rocks" Module (MVP)` must be completed, as tasks are fundamentally linked to Rocks.
   * Supabase project and client fully configured.

**7. Metrics for Success (Optional for Epic, but good for focus):**
   * User (self) successfully breaks down at least one Rock into several actionable tasks.
   * User (self) updates task statuses as work progresses.

**8. Notes / Assumptions:**
   * Task management will be relatively simple for MVP, focusing on the core CRUD operations and status updates directly within the context of a Rock.
   * Due dates are optional for tasks in the MVP.
   * The primary view for tasks will be within their parent Rock's detail page/section.
