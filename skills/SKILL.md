# Frontend Company Skill

## Purpose

Use this skill for all frontend development tasks in this organisation.

This skill enforces:

- approved folder structure
- file placement rules
- multi-client layout rules
- client-specific theme rules
- access management rules
- Redux rules
- service/API rules
- UI library delegation rules
- review checklist before final output

This skill is not responsible for teaching AntD, MUI, or Shadcn APIs.
For UI library implementation details, use the official UI library skill/docs when available.

## Project Stack

Default frontend stack:

- React
- Vite
- TypeScript
- Redux Toolkit
- RTK Query where applicable
- AntD / MUI / Shadcn depending on project selection
- Multi-client frontend architecture

## Core Rule

Before creating or modifying any file, first decide:

1. What is the feature?
2. Is it common or client-specific?
3. Which approved folder owns this file?
4. Is this UI, service, state, access, utility, config, or layout?
5. Is a new file necessary, or should an existing file be updated?

If ownership is unclear, do not create the file blindly.
Explain the best location first.

## Approved Folder Structure

See `folder-rules.md`.

## Multi-client Rules

See `multi-client-rules.md`.

## UI Library Rules

See `ui-library-rules.md`.

## Task Templates

See `task-templates.md`.

## Review Checklist

See `review-checklist.md`.

## Hard Rules

- Never create random folders.
- Never create files outside the approved structure.
- Never put API calls directly inside page components.
- Never put business logic inside client layouts.
- Never hardcode client-specific checks inside common pages.
- Never hardcode theme colors inside components unless explicitly requested.
- Never mix AntD, MUI, and Shadcn in the same component unless explicitly instructed.
- Avoid `any`. Use proper TypeScript types.
- Every reusable folder should expose exports through `index.ts` when useful.
- Do not duplicate server data into Redux unnecessarily.
- Do not create client-specific pages unless layout/config/theme/permissions cannot solve the difference.

## Standard Output After Work

After completing a frontend task, always return:

1. Files created/changed
2. Final file tree
3. Why each file belongs there
4. Assumptions made
5. Review checklist result
