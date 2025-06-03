# Commit Guidelines

This document outlines best practices for making clear, concise, and effective Git commits. Good commit hygiene is crucial for a maintainable and understandable project history.

## Core Principles of a Good Commit

*   **Atomic:** Each commit should represent a single logical change. Avoid bundling unrelated changes into one commit. This makes it easier to understand history, revert changes if necessary, and cherry-pick commits.
*   **Well-Described:** The commit message should clearly explain *what* changed and *why*.
*   **Tested & Verified:** The code in the commit should be in a working state.

## Pre-Commit Checklist

Before making a commit, ensure you have gone through the following steps:

1.  **Verify All Tests Pass:**
    *   Run all relevant unit tests, integration tests, and any other automated checks.
    *   A commit should ideally leave the codebase in a state where all tests are green.

2.  **Perform Code Quality Checklist:**
    *   Review your changes against the guidelines outlined in `CODE_QUALITY.md`.
    *   Ensure your code is readable, self-documenting, and adheres to project standards.

3.  **Self-Review Your Code:**
    *   Carefully review the diff of your changes (`git diff --staged` or using your IDE's diff viewer).
    *   Look for typos, debugging code left behind, commented-out old code, or any unintended modifications.
    *   Consider if the changes are complete and address the intended issue or feature appropriately.

4.  **Ensure Files End with a Newline:**
    *   Verify that all modified and new text files end with a single newline character. This is a common convention that helps prevent issues with some tools, diffs, and concatenation. Many editors can be configured to do this automatically.

5.  **Lint and Format Code:**
    *   Run linters to catch syntax errors, enforce coding standards, and identify potential issues.
    *   Use auto-formatters to ensure consistency with the project's agreed-upon style.

## Commit Message Structure

A well-structured commit message is vital. We follow a convention similar to Conventional Commits.

*   **Subject Line (Header):**
    *   **Format:** `<type>(<scope>): <short summary>`
        *   `<type>`: Describes the kind of change (e.g., `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`, `ci`, `build`).
        *   `<scope>` (Optional): Specifies the part of the codebase affected (e.g., `api`, `ui`, `parser`, a specific module name).
        *   `<short summary>`: A concise description of the change.
            *   Use the imperative mood (e.g., "Add user login" not "Added user login" or "Adds user login").
            *   Keep it short (ideally under 50 characters, but definitely under 72).
            *   Do not end with a period.
    *   **Examples:**
        *   `feat(auth): Implement password reset functionality`
        *   `fix(parser): Correct handling of empty input strings`
        *   `docs: Update installation instructions in README`
        *   `refactor(utils): Improve performance of data processing function`
        *   `test: Add unit tests for user service`

*   **Body (Optional):**
    *   If more explanation is needed beyond the subject line, include a body.
    *   Separate the subject from the body with a blank line.
    *   Explain the *what* and *why* of the changes in more detail.
    *   Wrap lines at 72 characters.
    *   Bullet points are okay for longer descriptions.
    *   Reference issue numbers if applicable (e.g., "Closes #42", "Fixes #123").

*   **Footer (Optional):**
    *   Used for breaking changes or referencing issues.
    *   **Breaking Changes:** Start with `BREAKING CHANGE:` followed by a description of the breaking change.
    *   **Issue Tracking:** `Refs: #123`, `Closes: #456`

**Example of a Full Commit Message:**

```
feat(api): Add endpoint for fetching user profiles

This commit introduces a new GET endpoint at /api/users/{id}/profile
which allows clients to retrieve detailed profile information for a
given user.

- Includes validation for the user ID.
- Returns a 404 if the user is not found.

Closes #78
```

By adhering to these commit guidelines, we create a project history that is easy to navigate, understand, and maintain. 