# Session Tracking Design Rules

This document outlines the structure and conventions for session tracking markdown files. These files are intended to capture the context, goals, and activity of a collaborative session, making it understandable for both AI agents and humans to review or continue the work.

## File Naming Convention

-   **Directory:** `notes/sessions/YYYY-MM-DD/` (where `YYYY-MM-DD` is the date the session was initiated).
-   **Format (within the dated directory):** `session-N.md`
    -   `N`: A sequential number for sessions started on the same date (e.g., `session-1`, `session-2`).

## Markdown File Structure & Template

The following template should be used for new session files:

'''markdown
# Session: YYYY-MM-DD - Session N

## Session Started:
- Date: YYYY-MM-DD
- Time: HH:MM (current time when session was initiated)

## Summary:
(A brief summary of the session's main activities, discussions, and outcomes. This is typically filled in or refined during the session finalization step.)

## Topics / Goals:
(A list of the primary topics discussed or the main goals of the session. This can be updated as the session progresses.)
- Example Topic/Goal 1
- Example Topic/Goal 2

## Notes / Activity Log:
(A chronological log of key activities, information shared, decisions made, or questions asked during the session. Entries should be concise and, where appropriate, timestamped or clearly ordered.)
- Session initiated.
- [HH:MM] User asked to work on X.
- Discussed approach Y for problem Z.
- Session ended at HH:MM (current time when session was finalized).
'''

## Key Information to Capture:

-   **Initial Prompt/Goal:** What triggered the session or what was the initial focus?
-   **Key Discussion Points:** Important ideas, questions, or decisions.
-   **Tasks Undertaken:** Any specific actions performed (e.g., "Agent drafted a document for X", "User provided feedback on Y").
-   **Contextual Information:** Links to relevant documents, code snippets, or external resources.
-   **Final Summary:** A concise overview of what was accomplished or discussed. 