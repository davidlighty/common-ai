# AI Agent Guide for the `common-ai` Repository

## 1. Overview

Welcome, AI Agent! This repository, `common-ai`, is designed to store common rules, workflows, and design documentation to ensure consistent and effective collaboration between humans and AI agents like yourself.

**Your primary instruction is to start by reading this guide and then follow the links provided to understand specific operational procedures and design principles. The summaries below will help you quickly understand the purpose of linked documents.**

## 2. Core Objective

The main goal of the documents herein is to provide clear, actionable guidance for tasks, content creation, and interaction patterns. By adhering to these guidelines, you will help maintain consistency, improve clarity, and streamline our collaborative efforts.

## 3. Key Documents & Starting Points

*   **Workflows (`WORKFLOWS.md`):**
    *   This is a critical document that outlines specific, step-by-step workflows for common tasks.
    *   **Action:** Please familiarize yourself with the workflows described in `[@WORKFLOWS.md](./WORKFLOWS.md)`. When a user's request matches a trigger pattern defined in a workflow, you **must prioritize** initiating and following that workflow.
    *   **Key Workflows Summary:**
        *   **Idea Breakdown:**
            *   **Purpose:** To take an idea, gather context, and guide the creation of a thorough design document (using `descriptions/DESIGN_DOC.md` as a template).
            *   **Trigger Pattern:** "I need to breakdown this idea [optional: about X]..."
        *   **Session Tracking:**
            *   **Purpose:** To create, manage, and finalize session documents that track context, goals, and progress. Uses `descriptions/SESSION_TRACKING_DESIGN.md` for structure.
            *   **Start Trigger Pattern:** "start new session", "begin new session", "let's start a new session".
            *   **End Trigger Pattern:** "finish and exit", "end session", "all done let's finish".

*   **Available Tools & Aliases (`TOOLS.md`):**
    *   This document lists available custom tools, scripts, and shell aliases that can be leveraged for development tasks.
    *   **Action:** Consult `[@TOOLS.md](./TOOLS.md)` to understand available automations and shortcuts that might be relevant to a user's request or for streamlining your own operations.
    *   **Key Tools Summary:**
        *   **`pru` (`~/code/dev-tools/cli/update-core-repos.sh`):**
            *   **Purpose:** Efficiently updates Git repositories and rebases feature branches, with conflict detection and safety measures.
            *   **Configuration:** Uses `~/.config/dev-tools/project-list.txt` and optional `to-rebase.txt` in repos.
        *   **`prr` (`~/code/dev-tools/cli/review-prs-improved.sh`):**
            *   **Purpose:** Generates a Markdown report of open GitHub Pull Requests and integrates it into a daily notes file.
            *   **Requirements:** `gh` (GitHub CLI) and `jq`.

*   **Design & Style Descriptions (`descriptions/` directory):**
    *   This directory contains detailed design guidelines and templates for various document types or processes.
    *   **Action:** Refer to the relevant files in the `[@descriptions/](./descriptions/)` directory when a workflow or task requires you to create or manage content that has a defined structure or style.
    *   **Key Description Files Summary:**
        *   **`DESIGN_DOC.md` (`[@descriptions/DESIGN_DOC.md](./descriptions/DESIGN_DOC.md)`):**
            *   **Purpose:** Provides best practices and a standard structure for creating design documents.
            *   **Key Sections:** Introduction, Problem Statement, Goals, Non-Goals, Proposed Solution, Alternatives, Impact, etc.
        *   **`SESSION_TRACKING_DESIGN.md` (`[@descriptions/SESSION_TRACKING_DESIGN.md](./descriptions/SESSION_TRACKING_DESIGN.md)`):**
            *   **Purpose:** Outlines the structure and conventions for session tracking markdown files created by the "Session Tracking" workflow.
            *   **Structure:** File naming (`YYYY-MM-DD-session-N.md` in `notes/`), sections for Summary, Topics/Goals, Activity Log.

*   **Code Quality Guidelines (`CODE_QUALITY.md`):**
    *   This document outlines best practices for writing high-quality code, emphasizing readability, self-documenting code, and maintainability.
    *   **Action:** Adhere to these guidelines when writing or reviewing code. Pay special attention to the principles of self-documenting code and minimizing unnecessary comments.
    *   **Key Principles Summary:**
        *   **Readability & Self-Documenting Code:** Prioritize clarity, use meaningful names, and structure code logically to reduce the need for comments.
        *   **Commenting:** Comment the *why*, not the *what*. Keep comments up-to-date and avoid clutter.
        *   **Maintainability:** Follow DRY, SRP, and aim for loose coupling.

*   **Pull Request Guidelines (`PULL_REQUEST_GUIDELINES.md`):**
    *   This document outlines best practices for creating clear and effective Pull Requests (PRs).
    *   **Action:** Follow these guidelines when creating or reviewing PRs to ensure they are informative and easy to review.
    *   **Key PR Practices Summary:**
        *   **Title/Header:** Make it descriptive; reference issues if applicable. Conventional prefixes (`feat:`, `fix:`) are good.
        *   **Summary/Description:** Use short, focused bullet points. Emoji use is okay (👍). No footers.
        *   **Content:** Clearly state the purpose, summarize changes, and include testing steps or visuals if needed.

## 4. General Principles for Interaction

*   **Clarity:** Strive for clear and unambiguous communication.
*   **Contextual Awareness:** Pay attention to the current context of the conversation and the files being worked on.
*   **Proactive Referencing:** When your actions are guided by a specific workflow or design document from this repository, please mention it (e.g., "Okay, I will initiate the 'Idea Breakdown' workflow," or "I will structure the session notes according to `descriptions/SESSION_TRACKING_DESIGN.md`.").
*   **Adherence to Structure:** When creating or modifying documents for which a template or structure is defined here, please adhere to that structure closely.
*   **Tooling Preference (GitHub CLI):** The GitHub CLI (`gh`) is installed and available. When interacting with GitHub repositories (e.g., managing pull requests, issues, gists), please prefer using `gh` commands over standard `git` commands if `gh` offers a more direct or efficient way to accomplish the task.

## 5. Evolution

These documents are living and will evolve. Always refer to the latest versions in this repository.

---

*This guide is your first point of reference. Follow the links to dive deeper.* 