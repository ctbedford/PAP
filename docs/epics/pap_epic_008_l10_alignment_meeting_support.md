**Epic Name:** EPIC: PAP-E08 - "L10 Alignment Meeting" Support Module (MVP)

**1. Epic Summary / Goal:**
   * To provide a structured template and note-taking facility to support the user in conducting their regular (e.g., weekly) "L10 Alignment Meeting." This module aims to help the user review progress, identify issues, and create commitments for the upcoming period, even in a solo context.

**2. Business Value / User Benefit (The "Why"):**
   * Facilitates a key PAP ritual: the structured weekly review and planning meeting (adapted for solo use).
   * Helps the user maintain momentum, address roadblocks, and ensure alignment with their Rocks and Painted Picture.
   * Provides a record of discussions, decisions, and commitments made during these review sessions.

**3. Scope:**
   * **In Scope (Key Deliverables/Features):**
        * Definition of a Supabase table schema for `L10Meetings` (e.g., user_id, meeting_date, notes_richtext_or_markdown, commitments_text_array).
        * A Next.js page (e.g., `/l10-meetings`) for starting a new L10 meeting (i.e., creating a new notes document from a template) and for viewing past meeting notes.
        * A predefined meeting template UI with sections (e.g., Check-in, Rock Review, Scorecard Review (conceptual for MVP), Issues List, IDS (Identify, Discuss, Solve), Commitments/To-Dos).
        * Use of a rich text editor (e.g., Tiptap or Markdown) for note-taking within each section of the meeting template.
        * Functionality to save the L10 meeting notes (including commitments) to Supabase.
   * **Out of Scope (For this Epic/MVP Release):**
        * Direct data integration from other modules into the L10 meeting notes (e.g., auto-populating Rock statuses or task lists). Data will be manually referenced or copied for MVP.
        * Automated scheduling or reminders for L10 meetings (user manages this externally for MVP).
        * Timer functionality for meeting sections.
        * Collaborative L10 meetings (MVP is single-user focused).
        * Assigning action items from commitments to specific tasks in the Tasks module automatically.

**4. Key Features / User Stories (Derived from original PAP tasks PAP-34 to PAP-38):**
   * `PAP-STORY-037`: As a user, I want to define the database structure (Supabase table) for my `L10Meeting` notes, including fields for the meeting date, structured notes (potentially rich text), and a list of commitments, so I can record my weekly reviews.
     * (Derived from PAP-34)
   * `PAP-STORY-038`: As a user, I want a dedicated page where I can start a new L10 Alignment Meeting (which creates a new note document from a template) and view my past L10 meeting notes, so I can manage this ritual.
     * (Derived from PAP-35)
   * `PAP-STORY-039`: As a user, when I start a new L10 meeting, I want to be presented with a template that includes standard sections like Check-in, Rock Review, Issues, IDS, and Commitments, and I want to use a rich text editor (or Markdown) to take notes in each section, so I can conduct a structured review.
     * (Derived from PAP-36)
   * `PAP-STORY-040`: As a user, I want to be able to save my L10 meeting notes, including any commitments I've made, to the database, so I have a persistent record of my meeting outcomes.
     * (Derived from PAP-38)
   * `PAP-STORY-041`: As a user conducting an L10 meeting, I will manually review my Rock statuses and other relevant data from other modules for MVP, rather than expecting automated data integration into the meeting notes.
     * (Derived from PAP-37)

**5. Acceptance Criteria (High-Level for Epic):**
   * User can create a new L10 Meeting note based on a predefined template.
   * User can input text (using rich text/markdown) into the various sections of the meeting template.
   * User can save the L10 Meeting notes, including any listed commitments, to Supabase.
   * User can view a list of past L10 Meeting notes and open one to read its content.
   * The UI for L10 meeting notes is usable for conducting a solo review session.

**6. Dependencies:**
   * `EPIC: PAP-E01 - User Authentication & Basic Account Setup (MVP)` must be completed.
   * Supabase project and client fully configured.
   * Rich Text Editor library (e.g., Tiptap) selected and basic integration planned.

**7. Metrics for Success (Optional for Epic, but good for focus):**
   * User (self) completes and saves notes for at least one L10 Alignment Meeting.
   * User (self) finds the template helpful for structuring their weekly review.

**8. Notes / Assumptions:**
   * The L10 Meeting structure is adapted from entrepreneurial operating systems (like EOS®) for a solo user context.
   * "Scorecard Review" section in the template might be conceptual for MVP if there's no dedicated scorecard module yet; user might note key metrics manually.
   * "Commitments" or "To-Dos" will likely be a simple text list within the notes for MVP, not directly linked to the main Tasks module automatically.
   * The focus is on providing the template and note-taking capability, not on full automation of the meeting process.
