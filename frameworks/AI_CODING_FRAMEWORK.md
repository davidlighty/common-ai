# AI Coding Framework

This document outlines the coding standards, rules, and best practices that an AI development agent must adhere to when performing software development tasks. It is derived from the `GENERAL_DEV_WORKFLOW.md` and aims to ensure consistency, quality, and maintainability in the codebase.

---

## I. Core Development Principles

1.  **Understand Requirements & Task Decomposition:**
    *   Always ensure a clear understanding of the assigned task, user stories, and acceptance criteria before writing code.
    *   If a task is complex or multifaceted, propose a breakdown into smaller, manageable sub-tasks.
    *   **Confirmation:** Present this sub-task breakdown to the user/supervisor for confirmation before proceeding.
    *   **Documentation:** Once confirmed, update the relevant task document (e.g., `DEV_TASK_LIST.md` or project backlog) with this breakdown, using a clear, hierarchical, and referenceable format (e.g., 1.1, 1.1.1, 1.1.2, 1.2).
    *   **Recursive Application:** Treat each confirmed sub-task as an individual task, reapplying this entire AI Coding Framework to its execution.
    *   Ask for clarification if any requirement (for the main task or any sub-task) is ambiguous.
2.  **Adhere to Project Standards:** Strictly follow project-specific guidelines, including chosen architecture, design patterns, coding style, and established conventions.
3.  **Write Clean, Readable Code:** Prioritize clarity and simplicity. Code should be self-documenting where possible. Use meaningful variable and function names.
4.  **Modularity & Reusability:** Design components and functions to be modular, reusable, and have single responsibilities (SOLID principles where applicable).
5.  **Self-Review for Composition & Style:** Before finalizing code, perform a self-review focusing on:
    *   **Composition:** Ensuring code is well-composed, favoring smaller, focused functions/modules over large, monolithic structures.
    *   **Anti-Monolithic Practices:** Actively avoiding monolithic code blocks and designs.
    *   **Style Consistency:** Maintaining a consistent coding style in line with project standards and the surrounding codebase.
6.  **Focused Task Execution & Quality Verification:** Concentrate on completing one discrete task at a time. Verify its successful completion, adherence to quality standards, and best practices before proceeding to the next task.
7.  **Test Thoroughly:** Write unit, integration, and UI tests as appropriate for all new code and changes. Aim for high test coverage.
8.  **Iterative Development:** Implement features incrementally. Seek feedback early and often if interacting with a human supervisor.
9.  **Security First:** Be mindful of security implications in all code. Follow secure coding practices (e.g., OWASP guidelines).
10. **Performance Awareness:** Write efficient code and be mindful of performance implications, especially in critical sections.
11. **Accessibility by Default:** Implement UI and functionality with accessibility (A11y) best practices in mind from the start.
12. **Comprehensive Documentation:** Document code (comments, docstrings), APIs, and complex logic where necessary. Keep project documentation updated.
13. **Version Control Discipline:** Follow Git best practices: frequent commits with clear messages, logical branches, and adherence to the project's branching strategy.
14. **Dependency Management:** Use approved libraries and manage dependencies carefully. Avoid unnecessary dependencies.
15. **Error Handling:** Implement robust error handling and provide clear, informative error messages.
16. **Idempotency:** Where applicable (e.g., API endpoints, background tasks), strive for idempotency.

---

## II. Phase-Specific Rules & Checklists

### A. Project Setup & Foundation

1.  **Environment Consistency:**
    - [ ] Ensure development environment matches project specifications.
    - [ ] Utilize project-defined environment variables and configurations.
2.  **Tooling Adherence:**
    - [ ] Strictly use the project's specified build tools, linters, and formatters.
    - [ ] Automatically apply linting and formatting rules before committing code.
3.  **Dependency Management:**
    - [ ] Verify all core dependencies are installed and correctly configured as per project guidelines.
    - [ ] Only add new dependencies after approval or if explicitly part of the task requirements.

### B. Architecture & Design Adherence

1.  **Architectural Compliance:**
    - [ ] Ensure all new code conforms to the established architectural pattern (MVC, MVVM, Microservices, etc.).
    - [ ] Do not introduce new architectural patterns without explicit approval.
2.  **Data Modeling:**
    - [ ] Follow defined data modeling practices and schema designs.
    - [ ] Ensure data integrity and implement validation as per specifications.
3.  **Component Design:**
    - [ ] Design components with clear responsibilities and well-defined interfaces.
    - [ ] Adhere to existing component structure and patterns.
4.  **API Design & Usage (Internal/External):**
    - [ ] **Provider:** When creating API endpoints, follow RESTful principles or GraphQL best practices as defined by the project. Ensure endpoints are secure, versioned, and well-documented (e.g., OpenAPI/Swagger).
    - [ ] **Consumer:** When using APIs, handle responses gracefully, including errors and different status codes. Implement proper data transformation and validation.

### C. Feature Development & Logic Implementation

1.  **Requirement Mapping:**
    - [ ] Ensure each piece of implemented logic directly maps to a specified requirement or user story.
2.  **Business Logic:**
    - [ ] Encapsulate business logic within appropriate service layers or modules.
    - [ ] Ensure logic is robust, handles edge cases, and is easily testable.
3.  **Modularity:**
    - [ ] Break down complex features into smaller, manageable, and testable modules/functions.
    - [ ] Ensure modules have clear inputs, outputs, and responsibilities.
4.  **Integration:**
    - [ ] Carefully integrate new features with existing systems and modules.
    - [ ] Verify data flow and interactions between integrated components.

### D. User Interface (UI) & User Experience (UX)

1.  **Design Fidelity:**
    - [ ] Implement UI elements to accurately match provided designs (wireframes, mockups, style guides).
2.  **Component Reusability:**
    - [ ] Utilize existing UI components from the project library whenever possible.
    - [ ] If new components are created, ensure they are generic and reusable.
3.  **Responsiveness & Adaptability:**
    - [ ] Ensure UI is responsive across specified devices and screen sizes.
4.  **State Management for UI:**
    - [ ] Manage UI state effectively, using local component state for local concerns and global state for shared application state.
5.  **User Input:**
    - [ ] Implement robust validation for all user inputs (client-side and server-side).
    - [ ] Provide clear feedback to the user regarding input status and errors.
6.  **Accessibility (A11y) in UI:**
    - [ ] Ensure interactive elements are keyboard accessible.
    - [ ] Provide appropriate ARIA attributes.
    - [ ] Ensure sufficient color contrast.
    - [ ] Include alt text for images.

### E. State Management (Global)

1.  **Predictable State:**
    - [ ] Adhere to the chosen state management pattern (Redux, Vuex, etc.) consistently.
    - [ ] Ensure state changes are predictable and traceable.
2.  **Immutability:**
    - [ ] If the state management library requires it (e.g., Redux), ensure state is treated as immutable.
3.  **Side Effects:**
    - [ ] Manage asynchronous operations and side effects according to the established patterns (sagas, thunks, services).

### F. Data Persistence

1.  **Data Integrity:**
    - [ ] Ensure data saved to local storage or backend systems is valid and consistent.
2.  **Security:**
    - [ ] Do not store sensitive information unencrypted in local storage.
    - [ ] Follow security best practices for all database interactions.
3.  **Efficiency:**
    - [ ] Optimize data queries and storage operations for performance.

### G. Testing & Quality Assurance

1.  **Unit Tests:**
    - [ ] Write unit tests for all new functions, methods, and components, focusing on business logic and edge cases.
    - [ ] Maintain high unit test coverage as per project goals.
2.  **Integration Tests:**
    - [ ] Write integration tests to verify interactions between components, modules, or services.
3.  **UI Tests (if applicable):**
    - [ ] Write tests to verify UI rendering, user interactions, and visual correctness.
4.  **Test Execution:**
    - [ ] Run all relevant tests before committing code and ensure they pass.
    - [ ] Integrate tests into the CI/CD pipeline.

### H. Code Quality & Maintenance

1.  **Code Comments & Docstrings:**
    - [ ] Add comments to explain complex logic, assumptions, or workarounds.
    - [ ] Write clear docstrings for public functions, classes, and modules.
2.  **Refactoring:**
    - [ ] Proactively refactor code to improve clarity, performance, or maintainability when appropriate and safe to do so.
    - [ ] Ensure refactoring does not alter external behavior and is covered by tests.
3.  **TODOs & FIXMEs:**
    - [ ] Use `TODO:` for planned enhancements and `FIXME:` for known issues needing correction. Include context or a ticket reference.
4.  **Dead Code:**
    - [ ] Remove commented-out or unused code before finalizing changes.

### I. Security

1.  **Input Validation:**
    - [ ] Validate all inputs from users or external systems (client-side and server-side).
2.  **Output Encoding:**
    - [ ] Properly encode output to prevent XSS vulnerabilities.
3.  **Authentication & Authorization:**
    - [ ] Implement and respect authentication and authorization mechanisms. Do not hardcode credentials.
4.  **Dependency Security:**
    - [ ] Regularly check for vulnerabilities in project dependencies.
5.  **Error Handling:**
    - [ ] Avoid leaking sensitive information in error messages.

### J. Performance

1.  **Efficient Algorithms:**
    - [ ] Use efficient algorithms and data structures.
2.  **Resource Management:**
    - [ ] Optimize resource usage (CPU, memory, network).
    - [ ] Avoid unnecessary computations or data transfers.
3.  **Lazy Loading:**
    - [ ] Implement lazy loading for assets and components where appropriate.

### K. Version Control

1.  **Commit Messages:**
    - [ ] Write clear, concise, and descriptive commit messages, following project conventions (e.g., Conventional Commits).
2.  **Branching Strategy:**
    - [ ] Adhere to the project's branching model (e.g., GitFlow, GitHub Flow). Create feature branches for new work.
3.  **Atomic Commits:**
    - [ ] Make small, atomic commits that represent a single logical change.
4.  **Pull Requests (PRs):**
    - [ ] If part of the workflow, create clear and descriptive PRs.
    - [ ] Ensure all checks (linting, tests, builds) pass before merging.

---

## III. Optional/Advanced Framework Considerations

These areas may require more specialized handling and could be expanded into their own detailed frameworks. The AI agent should be aware of these and seek specific guidance or use project-defined frameworks if available.

### A. Advanced QA: End-to-End (E2E) & Visual Testing

1.  **Applicability:**
    - [ ] Determine if E2E or visual regression testing is part of the project's QA strategy for the current task.
    - [ ] Identify key user flows or UI components that require E2E or visual testing.
2.  **Test Development (if tasked):
    - [ ] Use project-approved E2E testing frameworks (e.g., Cypress, Selenium, Playwright, Detox).
    - [ ] Write E2E tests that simulate real user scenarios and cover critical paths.
    - [ ] For visual testing, establish baseline images and use tools to detect visual discrepancies.
3.  **Test Execution & Analysis:**
    - [ ] Execute E2E and visual tests in the appropriate environments.
    - [ ] Analyze failures, differentiate between genuine bugs, test flakiness, or necessary baseline updates (for visual tests).
    - [ ] Report findings clearly, providing steps to reproduce and relevant artifacts (screenshots, logs).

### B. Commit Cadence & Strategy

1.  **User/Project Preference:**
    - [ ] Clarify the desired commit cadence with the user/supervisor or refer to project guidelines if available (e.g., commit per logical change, per sub-task, end-of-day summary commits for ongoing work).
2.  **Default Best Practice (if no specific guidance):
    - [ ] Favor atomic commits: each commit should represent a single, complete, logical unit of work that passes tests.
    - [ ] Commit frequently to save progress, especially when a small, verifiable piece of functionality is complete.
    - [ ] Avoid overly large commits that bundle unrelated changes.
    - [ ] Ensure commit messages are consistently styled and informative (refer to section II.K.1).
3.  **Work-in-Progress (WIP) Handling:
    - [ ] If committing incomplete work (e.g., for backup or handoff), clearly mark commits as WIP (e.g., using a `WIP:` prefix in the commit message) and avoid merging them to main/develop branches until complete and verified.

### C. Multi-Service Environment Management (for Microservices/Distributed Systems)

1.  **Environment Discovery & Documentation:**
    - [ ] Identify all relevant services in the distributed system.
    - [ ] Locate and understand documentation for starting, stopping, configuring, and verifying each service (e.g., `docker-compose.yml`, `Makefile`, `README.md` for each service).
2.  **Service Orchestration:**
    - [ ] Use provided scripts or tools (e.g., `docker-compose up -d`, `skaffold run`, custom shell scripts) to start all necessary services for the development/testing environment.
    - [ ] Understand the correct startup order if dependencies exist between services.
3.  **Health Verification:**
    - [ ] Know how to check the status and health of each service (e.g., checking logs, specific health check endpoints, `docker ps`).
    - [ ] Verify that all dependent services are running and healthy before proceeding with development or testing tasks that rely on them.
4.  **Resource Management:**
    - [ ] Be mindful of local system resources when running multiple services.
    - [ ] Stop services that are not currently needed to conserve resources, if appropriate and documented as safe.
5.  **Troubleshooting:**
    - [ ] Develop a basic strategy for troubleshooting common issues (e.g., port conflicts, configuration errors, service unavailability) by inspecting logs and service statuses.
    - [ ] Know when to escalate issues if unable to resolve service environment problems.

---

This framework is a living document and should be updated as development practices evolve and new project requirements emerge. 