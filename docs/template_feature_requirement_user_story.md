**Issue ID:** `[PAP-XX]`
**Issue Type:** [Feature / User Story / Task]

**Title:** [Clear, action-oriented title for the feature/story - e.g., "User Can Create and Manage 90-Day PAP Rocks"]

**Parent Epic:** `[Link to JIRA Epic - e.g., PAP Web App - MVP v1.0]`

**1. Description / User Story:**
   * **(If Feature):** (Provide a detailed description of the feature: what it does, why it's needed, and how it fits into the overall PAP app.)
   * **(If User Story):** As a [Meta-User of the PAP App], I want to [perform an action/achieve a goal with this feature] so that [I can achieve a specific benefit related to my PAP].
        * e.g., "As a Meta-User, I want to define, view, and update the status of my 90-Day Rocks so that I can maintain focus and track progress on my quarterly PAP objectives."

**2. Functional Requirements / Scope Details:**
   * (Break down the feature into specific functional pieces of what the system must do. Be specific.)
        * e.g., "System must allow creation of a Rock with fields for: Title, S.M.A.R.T. Objective, Measurables, Status (Not Started, In Progress, Done)."
        * e.g., "System must display all Rocks associated with the current 90-Day Cycle."
        * e.g., "User must be able to update the status of a Rock."

**3. User Interface (UI) / User Experience (UX) Considerations (Brief for MVP):**
   * (Key UI elements needed - e.g., "Input forms for Rock details," "List view for Rocks," "Dropdown for status change.")
   * (Brief description of the user flow - e.g., "User navigates to 'PAP Cycles & Rocks' module, selects current cycle, clicks 'Add Rock' button...")
   * (Reference any mockups or wireframes if you create them, even simple sketches.)

**4. Acceptance Criteria (AC):**
   * (A checklist of specific, testable conditions that must be met for this feature/story to be considered complete and working as intended. For personal use, bullet points are fine. Gherkin "Given/When/Then" can be used for more rigor if desired.)
        * AC1: Given I am on the "Current Cycle" page, When I click "Add Rock," Then a form appears with fields for Title, Objective, Measurables, and Status.
        * AC2: Given I have filled out the "Add Rock" form with valid data, When I click "Save Rock," Then the new Rock appears in the list for the current cycle with "Not Started" status.
        * AC3: Given a Rock exists, When I change its status to "In Progress," Then the status is updated and saved.
        * AC4: Given a Rock exists, When I change its status to "Done," Then the status is updated and saved.
        * AC5: (Error condition) Given I try to save a Rock without a Title, Then an error message is displayed, and the Rock is not saved.

**5. Non-Functional Requirements (NFRs) - MVP Context:**
   * (Consider essential NFRs even for an MVP.)
        * **Usability:** "The feature must be intuitive enough for me (the user) to use without extensive instructions."
        * **Performance (Basic):** "The page/feature should load within X seconds on a standard connection." (e.g., 3 seconds)
        * **Data Integrity:** "Data entered for this feature must be accurately saved to and retrieved from the Supabase database."

**6. Technical Notes / Implementation Details (Optional, for the developer - you):**
   * (Specific thoughts on implementation: e.g., "Use Supabase table 'Rocks'," "Next.js API route for saving Rock data," "Frontend component 'RockCard' using Shadcn/ui.")

**7. Dependencies:**
   * (Any other stories/features that must be completed first, or specific Supabase tables/functions that need to be in place.)
        * e.g., "User Authentication feature must be complete."
        * e.g., "'PAP Cycles' feature must allow for creation/selection of a cycle before Rocks can be added."

**8. Priority (for MVP):** [e.g., Must-Have, Should-Have, Could-Have]

**9. Estimate (Optional for personal project, but good practice):** [Rough estimate of time/effort]
