# Common AI Agent Guidelines (`common-ai`)

The purpose of this repository is to provide a comprehensive set of AI Agent rules, guidelines, workflows, and configurations. Our goal is to help everyone get a better start when using an AI agent, leading to a more productive, consistent, and enhanced collaborative experience.

These documents are designed to be read and understood by an AI agent, enabling it to align with project standards, follow common procedures, and apply best practices effectively.

## Key Features & Guidelines

This repository includes a suite of documents covering essential aspects of AI-assisted development and collaboration:

*   **`AI_AGENT_GUIDE.md`**: The central operational guide for the AI agent. It outlines all available documentation, references key workflows, lists global configurations (like the external knowledge base path), and summarizes the content of other critical files.
*   **Workflows (`WORKFLOWS.md`)**: Defines structured, step-by-step procedures for common tasks, including:
    *   **Idea Breakdown**: A process for taking an initial idea and developing it into a structured design document.
    *   **Session Tracking**: A workflow for documenting collaborative sessions, with instructions for the AI to attempt creating and managing notes in a specified external knowledge base (e.g., `~/notes/`).
*   **Tooling (`TOOLS.md`)**: Lists and describes available custom tools, scripts, and shell aliases that can be leveraged by the AI or user for development tasks.
*   **Design & Documentation Standards:**
    *   `descriptions/DESIGN_DOC.md`: Provides a template and guidelines for creating formal and comprehensive design documents.
    *   `descriptions/SESSION_TRACKING_DESIGN.md`: Details the structure and conventions for session tracking notes.
*   **Development Best Practices:**
    *   `CODE_QUALITY.md`: Outlines guidelines for writing clean, readable, and maintainable code, with a strong emphasis on self-documenting code and minimizing unnecessary comments.
    *   `COMMIT_GUIDELINES.md`: Specifies best practices for writing clear, concise, and effective Git commit messages, including a pre-commit checklist (testing, code quality, self-review, linting, etc.).
    *   `PULL_REQUEST_GUIDELINES.md`: Defines standards for creating informative Pull Requests that are easy to review, focusing on clear titles and bullet-point summaries.

## Getting Started

1.  **For AI Agents:** Your primary instruction is to thoroughly review and adhere to the `AI_AGENT_GUIDE.md`. This guide will direct you to other relevant documents and workflows based on the user's requests and the context of your interaction. Be mindful of instructions regarding operations on external directories (like the knowledge base), and always prioritize clear communication with the user if automated steps encounter issues.
2.  **For Users:** Familiarize yourself with the `AI_AGENT_GUIDE.md` to understand how the AI agent is configured to operate and what guidelines it follows. You can then leverage the defined workflows (e.g., by saying "start new session" or "I need to breakdown this idea") and expect adherence to the documented standards.

These documents are intended to be living and will evolve. Contributions and suggestions for improvement are welcome!
