**Epic Name:** EPIC: PAP-E07 - "Intellectual Blueprint" Repository (MVP)

**1. Epic Summary / Goal:**
   * To provide a dedicated module where users can create, store, and organize their "Intellectual Blueprints" – detailed notes, summaries, and structures of key concepts, learnings, and ideas. This serves as a personal knowledge base.

**2. Business Value / User Benefit (The "Why"):**
   * Supports the PAP principle of continuous learning and knowledge codification.
   * Enables users to build a structured repository of their most important intellectual assets, making them easily accessible for review and application.
   * Facilitates deeper understanding and retention of complex information by encouraging structured note-taking and synthesis.

**3. Scope:**
   * **In Scope (Key Deliverables/Features):**
        * Definition of a Supabase table schema for `Blueprints` (e.g., user_id, title, content_richtext_or_markdown, tags_array).
        * Next.js pages for listing existing Blueprints and for creating/editing individual Blueprints.
        * A form (using React Hook Form) for creating/editing a Blueprint, featuring a rich text editor (e.g., Tiptap or Markdown) for the main content.
        * Basic tagging functionality: allow users to add text tags to Blueprints.
        * Simple filtering or searching of Blueprints by title or tags (if feasible for MVP).
   * **Out of Scope (For this Epic/MVP Release):**
        * Inter-blueprint linking or graph views of knowledge.
        * File attachments or embedding multimedia within Blueprints (beyond what rich text editor supports).
        * Collaborative editing or sharing of Blueprints.
        * Version history for Blueprints.
        * Advanced search capabilities (e.g., full-text search beyond basic title/tag matching).

**4. Key Features / User Stories (Derived from original PAP tasks PAP-30 to PAP-33):**
   * `PAP-STORY-033`: As a user, I want to define the database structure (Supabase table) for my `Intellectual Blueprints`, including fields for a title, rich content, and tags, so I can store my structured knowledge.
     * (Derived from PAP-30)
   * `PAP-STORY-034`: As a user, I want dedicated pages to list all my Blueprints and to create or edit an individual Blueprint, so I can easily manage my knowledge repository.
     * (Derived from PAP-31)
   * `PAP-STORY-035`: As a user, I want to use a rich text editor (or Markdown editor) for the main content of my Blueprints, so I can create well-structured and formatted notes, diagrams, and summaries.
     * (Derived from PAP-32)
   * `PAP-STORY-036`: As a user, I want to be able to add tags to my Blueprints and potentially filter or search by these tags, so I can organize and find my knowledge more easily.
     * (Derived from PAP-33)

**5. Acceptance Criteria (High-Level for Epic):**
   * User can create a new Intellectual Blueprint with a title and rich text/markdown content.
   * User can add tags to a Blueprint.
   * Saved Blueprints are persisted in Supabase and associated with the correct user.
   * User can view a list of their Blueprints and open one for viewing/editing.
   * Basic filtering or searching by title/tag returns relevant Blueprints.
   * The UI for creating and viewing Blueprints is clear and usable.

**6. Dependencies:**
   * `EPIC: PAP-E01 - User Authentication & Basic Account Setup (MVP)` must be completed.
   * Supabase project and client fully configured.
   * Rich Text Editor library (e.g., Tiptap) selected and basic integration planned.

**7. Metrics for Success (Optional for Epic, but good for focus):**
   * User (self) creates multiple Blueprints for different concepts or areas of study.
   * User (self) finds the tagging and search/filter functionality useful for retrieving information.

**8. Notes / Assumptions:**
   * "Tags" will likely be implemented as an array of text strings for MVP.
   * Search/filter functionality will be basic for MVP (e.g., exact match or contains on title/tags).
   * The emphasis is on capturing structured text and simple formatting; complex embedding or media is out of scope for MVP.
