# Multi-client Rules

## Core Principle

Pages are common by default.

Client-specific differences should be solved in this order:

1. Theme
2. Config
3. Permission/access
4. Layout
5. Field rules
6. Client-specific component override
7. Client-specific page only as last option

Do not create client-specific pages unless the behaviour is truly different.

## Client Folder Ownership

src/clients/{client}

Use for:

- layout
- theme
- branding
- client config
- client-specific assets
- client-specific visual shell

Example:

src/clients/default
src/clients/clientA
src/clients/clientB

## Recommended Client Structure

src/clients/{client}/layout
src/clients/{client}/theme
src/clients/{client}/config
src/clients/{client}/assets

Optional only when required:
src/clients/{client}/components
src/clients/{client}/pages

## Layout Rules

Client layouts control:

- header
- sidebar
- menu
- logo
- page shell
- branding
- navigation
- layout-level permission visibility

Client layouts must not control:

- API calls
- business calculations
- form field business logic
- invoice calculations
- table business rules
- page-specific CRUD logic

## Common Page Rule

Common pages go inside:

src/pages

Example:

src/pages/purchase/PurchaseOrderPage.tsx

Common page can use:

- layout resolver
- theme provider
- access checks
- config-driven behaviour
- shared services

Common page must not contain:

- hardcoded client name checks
- hardcoded client colors
- raw dynamic import using client env path
- deeply nested client-specific if/else logic

## Layout Resolver Rule

Use resolver/registry pattern.

Preferred:

- src/clients/layoutRegistry.ts
- src/config/router/layoutResolver.tsx

The resolver must:

- select layout based on current client/org
- provide default fallback
- avoid raw dynamic path imports when possible

Bad:

import(`../../clients/${envConfig.org_name}/layout/ClientLayout.tsx`)

Good:

layoutRegistry[envConfig.org_name] ?? layoutRegistry.default

## Theme Rules

Client theme files go inside:

src/clients/{client}/theme

Theme resolver/provider files go inside:

src/config/theme

Theme must control:

- primary color
- secondary color
- typography
- radius
- component tokens
- CSS variables where applicable

Components must not hardcode tenant colors.

Bad:

if clientA, make button blue

Good:

button uses library default variant, theme decides color

## Config Rules

Client-specific config goes inside:

src/clients/{client}/config

Use config for:

- feature toggles
- menu visibility
- field visibility
- client labels
- branding metadata
- optional behaviour flags

Do not use config for:

- complex business logic
- API implementation
- large calculations

## Access Rules

Access must be handled through:

src/access

Use CanIAccess or access helper.

Do not hardcode:

user.role === 'admin'

Prefer:

CanIAccess module/action checks

## Client-specific Page Rule

Only create:

src/clients/{client}/pages

when:

- the page workflow is genuinely different
- config/layout/theme cannot solve it
- maintaining one common page would create unreadable code

Before creating client-specific page, explain why common page is insufficient.

## Decision Examples

### Example 1

Requirement:
Client A has different logo and sidebar color.

Decision:
Use client theme/layout.

Do not create new page.

### Example 2

Requirement:
Client B hides GST field on customer form.

Decision:
Use client field config.

Do not create new page.

### Example 3

Requirement:
Client C has a completely different invoice creation workflow.

Decision:
Client-specific page may be allowed.

Explain why.

## Final Rule

Keep 80 percent common.
Allow 20 percent client-specific override only when needed.

Duplication is expensive.
Over-generalisation is also expensive.
Choose the simplest clean solution.
