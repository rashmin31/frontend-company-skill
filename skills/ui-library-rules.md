# UI Library Rules

## Core Principle

This company skill does not teach UI library APIs.

For UI component details, use official skills/docs when available.

Company skill controls:

- where files go
- how UI components are organised
- how theme is applied
- how UI library selection is respected
- how not to mix libraries

## Supported UI Libraries

Supported project UI modes:

- Ant Design
- MUI
- Shadcn

A project should normally use one primary UI library.

## Hard Rules

- Do not mix AntD, MUI, and Shadcn in the same component unless explicitly instructed.
- Do not invent component props from memory.
- When unsure, check official docs/skills.
- Do not hardcode client colors in components.
- Prefer theme tokens, design tokens, or CSS variables.
- Keep common reusable components inside src/components.
- Keep client branding/theme inside src/clients/{client}/theme.

## Ant Design Rules

When uiLibrary is AntD:

Use:

- official Ant Design skill/docs
- official antd CLI skill if available
- AntD ConfigProvider for theme
- AntD theme tokens
- AntD components for enterprise CRUD screens

Common AntD components:

- Form
- Input
- Select
- Table
- Button
- Modal
- Drawer
- DatePicker
- Tabs
- Card
- Space
- Flex
- Typography
- Tag
- Tooltip
- Popconfirm
- message
- notification

Do not:

- use MUI or Shadcn components in AntD screens
- hardcode AntD colors inside components
- create custom components where AntD already solves the need cleanly
- guess deprecated props

Theme location:
src/clients/{client}/theme/antd.theme.ts

Theme resolver/provider:
src/config/theme

## MUI Rules

When uiLibrary is MUI:

Use:

- official MUI docs/skill if available
- MUI ThemeProvider
- MUI theme tokens
- MUI component system

Common MUI components:

- Box
- Stack
- Typography
- TextField
- Select
- Button
- Dialog
- Drawer
- Card
- Tabs
- Chip
- DataGrid where licensed/available

Do not:

- use AntD or Shadcn components in MUI screens
- hardcode client-specific colors
- bypass MUI theme when theme token is appropriate

Theme location:
src/clients/{client}/theme/mui.theme.ts

Theme resolver/provider:
src/config/theme

## Shadcn Rules

When uiLibrary is Shadcn:

Use:

- official Shadcn docs/skill if available
- Tailwind
- CSS variables
- small composed components

Common Shadcn components:

- Button
- Input
- Select
- Dialog
- Sheet
- Card
- Table
- DropdownMenu
- Form
- Checkbox
- Badge
- Tabs
- Command

Do not:

- use AntD or MUI components in Shadcn screens
- hardcode client colors in JSX
- create huge over-abstracted components
- ignore Tailwind/CSS variable theme system

Theme location:
src/clients/{client}/theme/shadcn.theme.css

Theme resolver/provider:
src/config/theme

## Reusable Component Rules

Reusable components go inside:

src/components

Suggested categories:

- ui
- forms
- tables
- modals
- feedback
- navigation

Examples:

- src/components/forms/CustomerForm.tsx
- src/components/tables/PurchaseOrderTable.tsx
- src/components/ui/AppButton.tsx

Components must not:

- call APIs directly
- contain tenant-specific branching
- contain page routing logic
- contain Redux store setup

## UI Decision Rule

Before creating UI, decide:

1. Which UI library is selected?
2. Is this page-level or reusable component?
3. Is the styling common or client-specific?
4. Should styling come from theme instead of inline style?
5. Is there an existing component to reuse?

## Output Rule

When creating UI, mention:

- selected UI library
- components used
- where theme is expected to come from
- why files were placed in chosen folders
