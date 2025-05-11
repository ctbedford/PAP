**Epic Name:** EPIC: PAP-E03 - "Painted Picture" Module (MVP)

**1. Epic Summary / Goal:**
   * To enable users to articulate, store, and regularly review their long-term vision (the "Painted Picture") across various life dimensions. This module aims to provide a dedicated space for this foundational self-actualization practice.

**2. Business Value / User Benefit (The "Why"):**
   * Supports a core tenet of the Principled Actualization Protocol: defining a clear, compelling future vision.
   * Provides the user with a persistent and easily accessible record of their Painted Picture, facilitating regular review and refinement.
   * Helps the user maintain alignment between their long-term aspirations and their current actions (as managed in other modules like Rocks and Tasks).

**3. Scope:**
   * **In Scope (Key Deliverables/Features):**
        * Definition of a Supabase table schema for storing Painted Picture dimensions (e.g., user_id, dimension_name, content, last_reviewed_at).
        * Creation of a Next.js page (e.g., `/vision/painted-picture`) with distinct sections for each of the (e.g., 8) predefined dimensions.
        * Implementation of a form (using React Hook Form) for each dimension, incorporating a Rich Text Editor (e.g., Tiptap, configured for essential formatting) or a Markdown editor to capture detailed content.
        * Functionality to save and update Painted Picture content for each dimension to the Supabase database (via client library or Next.js API route).
        * Display of a "Last Reviewed" timestamp for each dimension or for the overall Painted Picture.
        * A simple reminder mechanism or prompt for review (e.g., if last_reviewed_at is older than a set period).
   * **Out of Scope (For this Epic/MVP Release):**
        * User-defined custom dimensions for the Painted Picture.
        * Version history or tracking changes to the Painted Picture content.
        * Collaborative features or sharing of the Painted Picture.
        * AI-assisted generation or analysis of Painted Picture content.
        * Advanced visualization or graphical representation of the Painted Picture.

**4. Key Features / User Stories (Derived from original PAP tasks PAP-13 to PAP-17):**
   * `PAP-STORY-015`: As a user, I want to define the database structure (Supabase table) to store my Painted Picture content, including fields for different dimensions, rich text/markdown content, and a last reviewed date, so my vision is saved persistently.
     * (Derived from PAP-13)
   * `PAP-STORY-016`: As a user, I want a dedicated page in the web app where I can view and edit the different dimensions of my Painted Picture, so I have a central place for this activity.
     * (Derived from PAP-14)
   * `PAP-STORY-017`: As a user, I want to use a rich text editor (or Markdown editor) for each dimension of my Painted Picture, so I can format my vision effectively and capture detailed descriptions.
     * (Derived from PAP-15)
   * `PAP-STORY-018`: As a user, I want to be able to save my input for each Painted Picture dimension to the database and update it later, so my vision is always current.
     * (Derived from PAP-16)
   * `PAP-STORY-019`: As a user, I want to see when I last reviewed my Painted Picture (or each dimension), and receive a simple reminder if it's been a while, so I maintain engagement with my vision.
     * (Derived from PAP-17)

**5. Acceptance Criteria (High-Level for Epic):**
   * User can access a dedicated page for the Painted Picture.
   * User can input and save content for each predefined dimension using a rich text or markdown editor.
   * Saved content is persisted in the Supabase database and can be retrieved and displayed for editing.
   * A "Last Reviewed" timestamp is displayed and updates appropriately.
   * Basic UI is functional and allows for easy reading and editing of the Painted Picture content.

**6. Dependencies:**
   * `EPIC: PAP-E01 - User Authentication & Basic Account Setup (MVP)` must be completed.
   * Supabase project and client fully configured.
   * Rich Text Editor library (e.g., Tiptap) selected and basic integration planned.

**7. Metrics for Success (Optional for Epic, but good for focus):**
   * User (self) successfully populates all dimensions of their Painted Picture.
   * User (self) finds the interface intuitive for entering and reviewing their vision.

**8. Notes / Assumptions:**
   * The specific number and names of the Painted Picture dimensions (e.g., Health, Career, Relationships) will be predefined for the MVP.
   * The choice between a Rich Text Editor (like Tiptap) and a Markdown editor will be finalized during implementation, prioritizing ease of use and MVP scope.
   * The reminder mechanism will be very basic for MVP (e.g., a visual cue on the dashboard or page if not reviewed in X days).
