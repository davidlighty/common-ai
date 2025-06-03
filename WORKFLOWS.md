# Workflows

## Idea Breakdown

-   **Trigger Pattern:** "I need to breakdown this idea [optional: about X]..." (where X is the initial idea)
-   **Description:** "A workflow to take an idea, gain more context, and help create a thorough design document."

### Config:
-   **DESIGN_DOC_PATH:** `descriptions/DESIGN_DOC.md`

### Steps:

1.  **Action:** Create New Document
    *   **Details:** Create a new document. The initial title should be 'Idea Breakdown'. If an idea was provided in the trigger, append it to the title (e.g., 'Idea Breakdown - Creating a new western themed video game').
2.  **Action:** Clarify/Confirm Main Idea
    *   **Details:** If an idea was captured from the trigger pattern, present it to the user for confirmation or further clarification (e.g., "Okay, I understand you want to break down the idea: 'creating a new western themed video game'. Is that correct, or would you like to refine it?"). If no specific idea was captured, prompt the user: "What is the main idea or problem you want to break down?"
3.  **Action:** Gather Context
    *   **Details:** Prompt for additional details such as:
        *   What is the core problem you are trying to solve?
        *   Who is the target audience?
        *   What are the primary goals?
        *   What are the non-goals?
        *   Are there any existing solutions or approaches?
        *   What are the key success metrics?
4.  **Action:** Structure Design Document
    *   **Details:** Guide the user to structure their design document. Advise them to refer to the file specified in `DESIGN_DOC_PATH` (see Config section) for detailed guidelines and standard sections. Suggest incorporating the gathered context into the relevant sections of their new document (e.g., Problem Statement, Goals, etc., as outlined in `DESIGN_DOC_PATH`). The title should be "Idea Breakdown - [User's Idea/Problem]".
5.  **Action:** Iterate and Refine
    *   **Details:** Encourage review and iteration on the document. 

## Session Tracking

-   **Workflow Name:** Session Tracking
-   **Trigger Pattern (Start):** "start new session" (and similar phrases like "begin new session", "let's start a new session")
-   **Trigger Pattern (End):** "finish and exit", "end session", "all done let's finish" (and similar phrases like "wrap up session", "conclude session")
-   **Description:** "A workflow to create, manage, and finalize session documents that track the context, goals, and progress of collaborative work. This ensures that both AI agents and humans can easily understand the session's activities and resume work if needed."

### Config:
-   **SESSION_NOTES_DIR:** `notes/`
-   **SESSION_DESIGN_DOC_PATH:** `descriptions/SESSION_TRACKING_DESIGN.md`

### Steps:

1.  **Action:** Initiate Session
    *   **Trigger:** User initiates with a "start new session" type of prompt.
    *   **Details:**
        1.  Acknowledge the request: "Okay, starting a new session!"
        2.  Determine the current date (e.g., `2025-06-02`).
        3.  Check the directory specified in `SESSION_NOTES_DIR` (see Config section) for existing session files for the current date to determine the correct session number (e.g., if `SESSION_NOTES_DIR/2025-06-02-session-1.md` exists, the new file will be `SESSION_NOTES_DIR/2025-06-02-session-2.md`. If no files exist for the date, it will be `session-1`). The workflow should create the `SESSION_NOTES_DIR` if it doesn't exist.
        4.  Create a new markdown file in the `SESSION_NOTES_DIR`, following the structure and template outlined in `SESSION_DESIGN_DOC_PATH` (see Config section).
            *   **Filename format:** `YYYY-MM-DD-session-N.md` (e.g., `2025-06-02-session-1.md`).
        5.  Inform the user about the created file: "I've created a new session file at `[SESSION_NOTES_DIR]/YYYY-MM-DD-session-N.md` to track our work. It follows the guidelines in `SESSION_DESIGN_DOC_PATH`."
        6.  Prompt for initial context: "What is the main topic or goal for this session?"

2.  **Action:** Update Session Document (Ongoing)
    *   **Trigger:** Implicitly, throughout the user's interaction after a session has started.
    *   **Details:**
        1.  As the conversation progresses (e.g., user provides information, asks questions, new ideas are discussed, tasks are performed):
            *   Append concise entries to the "Notes / Activity Log" section of the *current* session markdown file (located in `SESSION_NOTES_DIR`). Entries should be timestamped or clearly denote the flow of work, as per `SESSION_DESIGN_DOC_PATH`.
            *   If the user explicitly states or clarifies a goal, add it to the "Topics / Goals" list in the current session file.
            *   Periodically, or when a significant sub-task is completed, the AI can internally try to update or refine a draft of the "Summary" section in the current session file.

3.  **Action:** Finalize Session
    *   **Trigger:** User initiates with an "end session" type of prompt.
    *   **Details:**
        1.  Acknowledge the request: "Okay, let's finalize this session."
        2.  Read the current content of the active session file (`[SESSION_NOTES_DIR]/YYYY-MM-DD-session-N.md`).
        3.  Prompt the user to review and update the session details as per `SESSION_DESIGN_DOC_PATH` (Summary, Topics/Goals).
            "Before we close this session, let's review and complete the session document.
            Current draft **Summary**: [Show current summary, or "Not yet drafted"]
            Current **Topics / Goals**:
            [List current topics/goals, or "None explicitly set"]

            Please provide a brief summary for this session. What were the key things we worked on or discussed?"
        4.  User provides input for the summary.
        5.  Ask for any final additions to topics/goals: "Are there any other specific topics or goals we should list for this session?"
        6.  User provides any additional topics/goals.
        7.  Update the "Summary" and "Topics / Goals" sections in the markdown file with the user's input.
        8.  Append a final entry to the "Notes / Activity Log" as per `SESSION_DESIGN_DOC_PATH`:
            ```markdown
            - Session ended at HH:MM (current time).
            ```
        9.  Save the finalized session document.
        10. Confirm finalization: "The session document `[SESSION_NOTES_DIR]/YYYY-MM-DD-session-N.md` has been updated and finalized. Ready for the next task when you are!" 