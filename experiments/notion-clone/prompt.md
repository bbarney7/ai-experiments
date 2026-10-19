Build a polished, functional Notion-style **web application** in one shot.

This must be a real web app with both:

- A complete user-facing UI/frontend
- A working backend/data layer that supports authentication, persistence, and multi-user/team usage

Do not build a desktop app, native Mac app, static mockup, design prototype, or frontend-only demo.

The goal is to build a real, usable productivity application that captures as much of the Notion experience and functionality as reasonably possible.

Assume this product will be used by a handful of small startup teams as a lightweight Notion replacement. This does not need to be enterprise-grade in terms of security, compliance, scalability, multi-region infrastructure, or operational complexity.

Design for a practical small-team SaaS product, not a hyperscale platform.

## Strict filesystem and code-access boundary

The directory `{{WORKSPACE}}` is the sole authorized local workspace for this task.

You and every subagent you delegate to must not access, search, list, inspect, read, copy, modify, execute, or use source code, repositories, project files, credentials, configuration, documentation, or other development artifacts located anywhere on this machine outside `{{WORKSPACE}}`.

Do not traverse parent directories, inspect sibling projects, search the home directory, consult recent-project metadata, or use files from any other local repository or workspace. If a path outside `{{WORKSPACE}}` appears in search results, logs, shell output, tool output, application state, or metadata, ignore it and do not open or traverse it.

This restriction applies equally to the primary agent, all subagents, and every tool or command they invoke. When delegating work, include this boundary explicitly in every subagent's instructions.

Normal operating-system executables, package managers, installed dependency runtimes, and agent tools may be invoked only as necessary to build and test the project, but their source code, configuration, caches, histories, and unrelated files outside `{{WORKSPACE}}` must not be inspected or used as project input.

Public web research and downloading ordinary open-source packages through their standard package managers remain allowed. All project work and generated artifacts must stay inside `{{WORKSPACE}}`.

If required project material is not available inside `{{WORKSPACE}}`, continue with safe work using only the authorized directory and public web resources, then report the limitation. Do not search elsewhere on the machine for it.

## Your role

You are the primary orchestrator and planner for this task.

Your responsibilities are to:

- Research the product
- Plan the work before implementation
- Break the project into clear workstreams
- Delegate implementation work to capable subagents running on lower-cost models whenever the environment allows you to choose the subagent model
- Coordinate subagents so their work fits together into one coherent application
- Review and validate their output
- Identify incomplete, buggy, low-quality, or conflicting implementation
- Send targeted follow-up work back to subagents when needed
- Integrate the final result into a polished, working product

Your default behavior should be to orchestrate and delegate rather than personally implement large portions of the application.

If a subagent's work does not meet your standards, first try to correct the issue through better instructions or follow-up delegation.

You may step in and implement or fix work yourself when necessary, but ideally this should be the exception.

You remain responsible for the quality of the final product regardless of which agent performed the implementation.

## Research

Before creating the implementation plan, use the web to research Notion's current product, functionality, interaction patterns, and UX.

Use that research to understand what Notion currently supports and which features are most valuable to reproduce.

You may consult:

- Notion's official website
- Notion's help and documentation
- Public product pages
- Public screenshots and demos
- Other web-accessible references that help you understand the product

You may reproduce publicly observable Notion interaction patterns and product behavior.

Do not copy proprietary Notion source code or proprietary assets.

Do not use an existing Notion clone as a shortcut for this benchmark.

## Open-source libraries and dependencies

You may freely use open-source libraries, packages, components, frameworks, utilities, and design resources when they help you build a better product.

This includes, but is not limited to:

- Icon libraries
- UI component libraries
- Design systems
- CSS frameworks
- Styling libraries
- Typography libraries
- Animation libraries
- Drag-and-drop libraries
- Rich-text and block-editor libraries
- Markdown libraries
- Database clients
- State-management libraries
- Authentication helpers
- File-upload libraries
- Search libraries
- Date/time utilities
- Testing libraries
- Other general-purpose open-source dependencies

General-purpose editor frameworks such as TipTap, Lexical, ProseMirror, BlockNote, Slate, or similar libraries are explicitly allowed.

You are encouraged to use strong existing building blocks rather than reimplementing commodity functionality from scratch when doing so improves the final product.

The major exception is existing Notion clones or projects whose primary purpose is to recreate Notion.

Do not use, copy from, install, fork, inspect, or adapt an open-source Notion clone, Notion recreation, or substantially complete Notion-like application as the basis for this work.

## Planning artifacts

Before implementation, create markdown planning files in the project that document your approach.

At minimum, create:

- `PLAN.md` — overall product, architecture, implementation, and sequencing plan
- `TASKS.md` — work breakdown, delegated tasks, ownership, dependencies, and status
- `DECISIONS.md` — important product, UX, architecture, and technical decisions

Keep these files reasonably current as the work progresses so they are useful for reviewing your planning and orchestration afterward.

Document meaningful delegation decisions, major changes in direction, and significant cases where you had to step in because delegated work did not meet the required standard.

These files are part of the benchmark output and should remain in the project when the work is complete.

Documentation should not take priority over building and improving the product.

## Product scope

Implement as much meaningful Notion functionality as reasonably possible.

Do not stop simply because the minimum requirements have been satisfied.

Once the core experience is reliable, continue adding the highest-value Notion-like functionality you can reasonably complete.

Potential functionality includes, but is not limited to:

- Pages and nested pages
- Favorites
- Recently viewed pages
- Search
- Workspace navigation
- Page icons
- Page covers
- Breadcrumbs
- Block-based editing
- Rich-text formatting
- Headings
- Bulleted lists
- Numbered lists
- Checklists
- Quotes
- Code blocks
- Dividers
- Callouts
- Toggles
- Links
- Images
- File attachments
- Tables
- Simple databases
- Database properties
- Table views
- Board/Kanban views
- Filtering
- Sorting
- Page templates
- Slash commands
- Drag-and-drop block reordering
- Block duplication
- Block deletion
- Block conversion
- Keyboard shortcuts
- Workspace/team membership
- Page sharing within a workspace
- Comments or lightweight collaboration
- Trash and recoveryfff
- Dark mode
- Responsive layouts
- Persistent user preferences

Do not treat this list as exhaustive.

Use your research and product judgment to identify other features that would make the application feel more like a real Notion replacement.

Favor complete, genuinely working features over fake, decorative, or partially implemented ones.

## Core product requirements

At minimum, the application should include:

- User sign-up, login, logout, and session persistence
- A workspace/team concept suitable for small startup teams
- A workspace sidebar with pages
- Nested pages
- Create, rename, delete, and navigate between pages
- A block-based document editor
- Multiple block types, including at minimum:
  - Paragraph
  - Heading
  - Bulleted list
  - Numbered list
  - Checklist
  - Quote
  - Code block
- A slash-command menu for inserting blocks
- Ability to reorder blocks
- Natural keyboard behavior for creating, deleting, and navigating between blocks
- Page titles and icons
- Search for finding pages
- Light and dark mode
- Persistent data that survives refreshes and is available across sessions
- A responsive, polished interface

Seed the application with a realistic example workspace so it feels complete when it first launches.

## Editor quality

Pay particular attention to the editor experience.

Typing, pressing Enter, pressing Backspace, navigating between blocks, opening slash commands, changing block types, and reordering content should feel natural and reliable.

The editor should feel like an actual productivity tool, not a collection of disconnected form controls.

## Visual and interaction fidelity

Visual fidelity is part of the experience.

Pay attention to:

- Overall layout
- Information density
- Sidebar behavior
- Editor width
- Typography
- Spacing
- Menus
- Icons
- Hover states
- Contextual controls
- Empty states
- Modals and popovers
- Motion and transitions
- Keyboard behavior
- Responsive behavior

The finished product should feel recognizably inspired by Notion while remaining an independently implemented product.

## Authentication and user management

Firebase must be used for authentication and user management.

Firebase credentials/configuration for the `{{FIREBASE_PROJECT_ID}}` project are available in files in the project's root directory.

Use only the Firebase project named `{{FIREBASE_PROJECT_ID}}`. Do not discover, list, inspect, read, access, modify, or use any other Firebase project or any configuration, credentials, files, CLI state, environment variables, or resources associated with another Firebase project.

Use Firebase Authentication for:

- User registration
- Login
- Logout
- Session persistence
- Identifying the current user
- Basic account/user identity functionality needed by the application

Choose the authentication methods that make the most sense based on the Firebase configuration available to you.

Keep authentication simple and practical.

This product is intended for a small number of startup teams, so do not over-engineer identity management.

You do not need to implement enterprise features such as:

- SAML
- SCIM
- Complex RBAC systems
- Enterprise audit infrastructure
- Multi-region identity architecture
- Advanced compliance controls

Basic, sensible authorization between users, workspaces, and their data is sufficient.

Do not expose Firebase Admin credentials or other privileged server credentials to browser code.

## Application backend and persistence

Supabase credentials/configuration for the `{{SUPABASE_PROJECT_ID}}` project are also available in files in the project's root directory.

Use only the Supabase project named `{{SUPABASE_PROJECT_ID}}`. Do not discover, list, inspect, read, access, modify, or use any other Supabase project or any configuration, credentials, files, CLI state, environment variables, database resources, or other resources associated with another Supabase project.

Firebase authentication is required, but you may decide how to implement the rest of the backend.

You may use:

- Firebase Authentication with Firestore for application data
- Firebase Authentication with Supabase for application data
- Firebase Authentication with another sensible architecture using the resources already available in the project

Make the technical choice you believe produces the best application.

You may create the schemas, tables, collections, policies, indexes, or other resources needed for the application if your available access permits it.

The backend must actually support the application rather than acting as a placeholder.

Data created by users should persist and be available across sessions.

Persist meaningful workspace state such as:

- Users
- Workspaces/teams
- Workspace membership
- Pages
- Nested page relationships
- Document blocks
- Block ordering
- Page titles
- Page icons
- Database content
- User preferences
- Other relevant workspace and document state

Prefer straightforward architecture that is reliable and appropriate for a few small startup teams.

Do not over-engineer the backend for hypothetical massive scale.

## Cost constraints

Do not enable, upgrade, or change Firebase, Supabase, hosting, database, storage, or any other service to a paid tier.

Do not perform any action that introduces a new recurring charge or increases the project's billing tier.

Stay within the resources and free-tier capabilities already available to you.

Do not create new paid projects or paid infrastructure.

If a desired implementation would require upgrading a service or creating additional cost, choose a simpler implementation instead.

## Important project constraints

Strictly isolate this task to the authorized project resources:

- The only authorized Supabase project is `{{SUPABASE_PROJECT_ID}}`.
- The only authorized Firebase project is `{{FIREBASE_PROJECT_ID}}`.
- Do not enumerate projects or accounts in either service to find alternatives.
- If the authorized configuration is missing, invalid, or insufficient, continue with safe local work where possible and report the limitation; do not inspect or use another project.

Do not use Syntaur in any way. Do not invoke Syntaur tools, skills, commands, plugins, workflows, missions, assignments, plans, context, or protocol files.

Do not look for, inspect, read, modify, or create any Syntaur files or resources, including anything under `~/.syntaur/` or any `.syntaur/` directory.

Do not use Syntaur assignments as a source of instructions, context, requirements, or prior work for this task.

Do not access, search, list, inspect, read, modify, execute, or use the `{{COMPARISON_WORKSPACE_NAME}}` directory anywhere on this machine or any files or resources inside it. If it appears in search results, directory listings, recent-project metadata, or tool output, ignore it and do not open or traverse it.

Do not use any installed design skills, UI/UX skills, visual design skills, frontend design skills, style guides, design-system skills, or similar helper skills available in the environment.

Do not inspect or invoke those installed design-related skills for inspiration, instructions, patterns, components, or implementation guidance.

This restriction applies specifically to installed agent skills.

It does not prevent you from using normal open-source libraries, icon sets, component libraries, design systems, CSS frameworks, editor frameworks, or other general-purpose dependencies.

The design and UX should come from your own reasoning, public web research, and implementation decisions based on this prompt.

Work only from this prompt, relevant public web research, the existing project files needed to build the application, the planning files you create, and the Firebase/Supabase configuration available in the project root.

## Execution and quality bar

Do not ask me questions.

Do not stop at a prototype, plan, or partial implementation.

Plan the work, research the product, orchestrate implementation through subagents, review the output critically, correct problems, integrate the pieces, run the application, interact with it, and test it before considering the task complete.

Do not consider the task finished merely because:

- The application compiles
- Automated tests pass
- The minimum requirements have been implemented
- The main screen renders successfully

Before finalizing the application, use it as a real user would.

Test important user journeys end-to-end, including:

- Creating an account and logging in
- Logging out and back in
- Creating and navigating a workspace
- Creating pages
- Nesting pages
- Renaming and deleting pages
- Editing documents with multiple block types
- Using slash commands
- Using important keyboard interactions
- Reordering content
- Searching and navigating
- Refreshing the application and verifying persistence
- Confirming the correct user's data remains available across sessions
- Testing important menus, popovers, dialogs, and contextual controls
- Testing light and dark mode
- Checking the application at different browser sizes

Inspect the actual rendered UI during development and fix obvious visual, interaction, layout, and usability problems.

Continue improving the application after the minimum feature set is complete if there are meaningful Notion-like features you can still implement reliably.

You will be judged on one thing:

**How close the finished product—functionally, visually, and interactively—feels to using a real Notion replacement.**
