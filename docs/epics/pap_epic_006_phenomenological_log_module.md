**Epic Name:** EPIC: PAP-E06 - "Phenomenological Log" Module (MVP)

**1. Epic Summary / Goal:**
   * To provide users with a dedicated space to create, store, and review daily phenomenological log entries. This module supports the practice of self-reflection, insight generation, and emotional processing, which are key to the PAP.

**2. Business Value / User Benefit (The "Why"):**
   * Enables a core PAP practice: regular, structured reflection on personal experience.
   * Helps users identify patterns, triggers, and insights over time, contributing to self-awareness and growth.
   * Provides a private and secure digital journal for sensitive personal reflections.

**3. Scope:**
   * **In Scope (Key Deliverables/Features):**
        * Definition of a Supabase table schema for `LogEntries` (e.g., user_id, entry_date, state_rating, triggers, experience, techniques_used, outcome, insights_richtext_or_markdown).
        * A Next.js page (e.g., `/log`) for creating new log entries and for viewing a chronological list of past entries.
        * A form (using React Hook Form) for creating new log entries, including fields for predefined phenomenological categories and a rich text editor (e.g., Tiptap or Markdown) for detailed insights/reflections.
        * Chronological listing of past log entries, possibly with basic date filtering or pagination for MVP.
   * **Out of Scope (For this Epic/MVP Release):**
        * Advanced search or tagging of log entries.
        * Sentiment analysis or AI-driven insights from log content.
        * Graphical representation of mood/state ratings over time.
        * Exporting log entries to other formats (e.g., PDF, TXT).
        * Customizable log entry templates or fields.

**4. Key Features / User Stories (Derived from original PAP tasks PAP-26 to PAP-29):**
   * `PAP-STORY-029`: As a user, I want to define the database structure (Supabase table) for my `LogEntries`, including fields for entry date, various experiential dimensions (state rating, triggers, experience, techniques, outcome), and a rich text/markdown field for insights, so I can capture my reflections systematically.
     * (Derived from PAP-26)
   * `PAP-STORY-030`: As a user, I want a dedicated page where I can create new daily log entries and view my past entries in chronological order, so I can easily manage my journal.
     * (Derived from PAP-27)
   * `PAP-STORY-031`: As a user, I want a form with specific fields for the key phenomenological categories and a rich text editor (or Markdown editor) for the main insights/reflections part of my log entry, so I can capture comprehensive information.
     * (Derived from PAP-28)
   * `PAP-STORY-032`: As a user, I want to see my past log entries listed chronologically, possibly with simple date navigation or filtering, so I can review my journey over time.
     * (Derived from PAP-29)

**5. Acceptance Criteria (High-Level for Epic):**
   * User can create a new phenomenological log entry with data for all defined fields, including rich text/markdown insights.
   * Saved log entries are persisted in Supabase and associated with the correct user and date.
   * User can view a list of their past log entries, ordered by date (most recent first).
   * The UI for creating and viewing log entries is clear and usable.

**6. Dependencies:**
   * `EPIC: PAP-E01 - User Authentication & Basic Account Setup (MVP)` must be completed.
   * Supabase project and client fully configured.
   * Rich Text Editor library (e.g., Tiptap) selected and basic integration planned (if chosen over Markdown).

**7. Metrics for Success (Optional for Epic, but good for focus):**
   * User (self) creates log entries regularly (e.g., daily or several times a week).
   * User (self) finds the logging process easy and the collected information valuable for reflection.

**8. Notes / Assumptions:**
   * The specific fields for the phenomenological log (state_rating, triggers, etc.) are predefined for MVP based on the PAP methodology.
   * "State rating" might be a simple integer scale (e.g., 1-10) for MVP.
   * Rich text capabilities for the 'insights' field are important for capturing nuanced reflections; Tiptap or a similar lightweight editor is preferred if feasible for MVP scope.
