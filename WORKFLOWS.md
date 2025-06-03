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
-   **Trigger Pattern (Start):** "start new session" (and similar phrases like "begin new session", "let\'s start a new session")
-   **Trigger Pattern (End):** "finish and exit", "end session", "all done let\'s finish" (and similar phrases like "wrap up session", "conclude session")
-   **Description:** "A workflow to manage and document collaborative work sessions. It attempts to create session notes in the user\'s specified external knowledge base. If automated creation fails, it will guide the user to do so manually."

### Config:
-   **SESSION_DESIGN_DOC_PATH:** `descriptions/SESSION_TRACKING_DESIGN.md` 
    (Note: `KNOWLEDGE_BASE_NOTES_DIR` is now globally defined in `AI_AGENT_GUIDE.md`)

### Steps:

1.  **Action:** Initiate Session
    *   **Trigger:** User initiates with a "start new session" type of prompt.
    *   **Details:**
        1.  Acknowledge the request: "Okay, starting a new session!"
        2.  Attempt to retrieve `KNOWLEDGE_BASE_NOTES_DIR_VALUE` from the 'Global Configuration' section of `AI_AGENT_GUIDE.md` (e.g., `~/notes/`). If not found or path is invalid, inform user and stop workflow, suggesting manual note-taking.
        3.  Determine the current date string in `YYYY-MM-DD` format (e.g., `2023-10-27`). Let this be `CURRENT_DATE_STR`.
        4.  **AI Action for Path Expansion:** Programmatically expand `KNOWLEDGE_BASE_NOTES_DIR_VALUE` to an absolute path. For instance, if it starts with `~/`, replace `~` with the user's actual home directory (e.g., `/home/dlighty`). Let the result be `ABS_KNOWLEDGE_BASE_NOTES_DIR`. If expansion is not possible or fails, inform the user and fall back to guiding manual note creation.
        5.  Construct the absolute target session directory path: `ABS_KNOWLEDGE_BASE_NOTES_DIR` + `sessions/` + `CURRENT_DATE_STR` + `/` (e.g., `/home/dlighty/notes/sessions/2023-10-27/`). Let this be `ABS_TODAYS_SESSION_DIR`.
        6.  **Attempt to create directory:** Try to ensure `ABS_TODAYS_SESSION_DIR` exists using a command like `mkdir -p "[ABS_TODAYS_SESSION_DIR]"`. (Quotes are generally safe here as the path is now absolute and won't have shell expansion issues with `~`).
            *   **If successful:** Proceed.
            *   **If failed (e.g., due to permissions or tool limitations):** Inform the user: "I was unable to create the directory `[ABS_TODAYS_SESSION_DIR]`. Please create it manually." Then, prompt: "Once the directory is ready, or if you prefer to use a different path for today\'s session notes, please provide the full directory path." If user provides a path, use it for `ABS_TODAYS_SESSION_DIR`; otherwise, fall back to guiding manual note creation.
        7.  Determine the next session number (`N`) for `CURRENT_DATE_STR` by checking for existing `session-*.md` files in `ABS_TODAYS_SESSION_DIR`. This may require tools to list external directories; if unable, assume `N=1` and inform the user, or ask the user for `N`.
        8.  Construct the new session filename: `session-N.md`. Let this be `SESSION_FILENAME`.
        9.  The full path to the new session file will be `ABS_TODAYS_SESSION_DIR` + `SESSION_FILENAME`. Let this be `ABS_SESSION_FILE_PATH`.
        10. **Attempt to create session file:** Try to create a new markdown file at `ABS_SESSION_FILE_PATH`, using the template from `SESSION_DESIGN_DOC_PATH`.
            *   **If successful:** Inform the user: "I\'ve attempted to create a new session file at `[ABS_SESSION_FILE_PATH]`. It follows the guidelines in `SESSION_DESIGN_DOC_PATH`."
            *   **If failed:** Inform the user: "I was unable to create the session file at `[ABS_SESSION_FILE_PATH]`. Please create it manually using the template from `SESSION_DESIGN_DOC_PATH`." Then provide the template content.
        11. Prompt for initial context: "What is the main topic or goal for this session?"
        12. Store `ABS_SESSION_FILE_PATH` as the active session file for this workflow instance.

2.  **Action:** Update Session Document (Ongoing)
    *   **Trigger:** Implicitly, throughout the user\'s interaction after a session has started.
    *   **Details:**
        1.  Refer to the active `ABS_SESSION_FILE_PATH`.
        2.  As the conversation progresses, AI *may suggest* content to append to the "Notes / Activity Log" or "Topics / Goals" sections.
        3.  **Note for AI Agent:** Directly appending to an external file at `ABS_SESSION_FILE_PATH` might be restricted. If so, provide the suggested text to the user and instruct them to manually append it to their session note at `[ABS_SESSION_FILE_PATH]`.
            *   Example: "To update your session log, please add: \'- [HH:MM] Discussed X.\'"

3.  **Action:** Finalize Session
    *   **Trigger:** User initiates with an "end session" type of prompt.
    *   **Details:**
        1.  Acknowledge the request: "Okay, let\'s finalize this session."
        2.  Refer to the active `ABS_SESSION_FILE_PATH`.
        3.  **Note for AI Agent:** Reading the external file at `ABS_SESSION_FILE_PATH` might be restricted. If unable to read, proceed by asking the user for current summary/goals.
        4.  Attempt to read the current content of `ABS_SESSION_FILE_PATH`.
        5.  Prompt the user to review and provide the final "Summary" and "Topics / Goals" for the session document at `[ABS_SESSION_FILE_PATH]`.
            "Before we close this session, please review your session document at `[ABS_SESSION_FILE_PATH]`.
            What is a brief summary for this session? What were the key things we worked on or discussed?"
            (If content was read: "Current draft **Summary**: [Show current summary, or "Not yet drafted"]...")
        6.  User provides input for the summary and any final topics/goals.
        7.  **Note for AI Agent:** Directly updating the external file might be restricted. If so, provide the formatted "Summary", "Topics/Goals", and final "Session ended" log entry to the user, instructing them to update `[ABS_SESSION_FILE_PATH]`.
        8.  If direct update is possible, update the relevant sections and add the final log entry:
            \'\'\'markdown
            - Session ended at HH:MM (current time).
            \'\'\'
        9.  Confirm action: "Please ensure your session document `[ABS_SESSION_FILE_PATH]` is updated with the final summary, goals, and closing entry. Ready for the next task when you are!" 