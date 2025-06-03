# Available Tools & Aliases

This document lists available custom tools and shell aliases that can be leveraged for development tasks. Understanding these tools can help AI agents assist more effectively.

## Shell Aliases

The following aliases are configured in the user's shell environment (e.g., `.zshrc` or `.bashrc`):

-   **`pru`**: Alias for `~/code/dev-tools/cli/update-core-repos.sh`. See details below.
-   **`prr`**: Alias for `~/code/dev-tools/cli/review-prs-improved.sh`. See details below.

## Script Details

### `pru` (`~/code/dev-tools/cli/update-core-repos.sh`)

-   **Purpose:** A script for safe and efficient Git repository maintenance, primarily for updating multiple repositories and rebasing feature branches.
-   **Key Features:**
    -   Batch updates repositories defined in `~/.config/dev-tools/project-list.txt`.
    -   Can also target a single repository/branch or PR URL.
    -   Fetches the latest from the `master` branch (or a configured base branch).
    -   Intelligently rebases local feature branches (found in a `to-rebase.txt` file within each repo, or auto-detected) onto the updated base branch.
    -   Includes pre-flight conflict detection to avoid broken states.
    -   Manages uncommitted changes by stashing and unstashing.
    -   Provides detailed logging and offers various command-line options for customized behavior (e.g., `--verbose`, `--dry-run`, `--no-force-push`).
-   **Primary Configuration:** `~/.config/dev-tools/project-list.txt` (for repository list) and optional `to-rebase.txt` in each repository for specific branches to rebase.
-   **Safety:** Designed with safety first, aiming to always leave repositories in a clean state and aborting conflicting rebases.

### `prr` (`~/code/dev-tools/cli/review-prs-improved.sh`)

-   **Purpose:** Generates a Markdown report of open Pull Requests (PRs) from configured repositories and integrates this into a daily notes file.
-   **Key Features:**
    -   Uses GitHub CLI (`gh`) to fetch open PR data for repositories listed in `~/.config/dev-tools/project-list.txt` (or other configured locations).
    -   Categorizes PRs by their current status (e.g., Needs Review, Approved, Draft).
    -   Formats the PR list into a Markdown report.
    -   Designed to update a specific section within a daily notes file, marked by a header (`# Daily Notes`) and a separator (`--- 📋 PR Review End ---`). Content outside these markers is preserved.
    -   Supports an optional template file for content that should follow the PR review section in the daily notes.
-   **Requirements:** `gh` (GitHub CLI) and `jq` must be installed and configured.
-   **Primary Configuration:** 
    -   Repository list (e.g., `~/.config/dev-tools/project-list.txt`).
    -   A daily notes file structured with the specific header and separator.
-   **Output:** Modifies the target daily notes file by inserting the PR review report. 