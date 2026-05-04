# Task Templates

Use these templates when performing frontend development tasks.

## Template 1: Create Common Page

Use when creating a route-level page shared across clients.

Inputs:

- page name
- domain
- UI library
- required features
- permissions
- API/service requirement
- Redux requirement if any

Rules:

- Page goes inside src/pages/{domain}
- Reusable components go inside src/components/{category}
- API logic goes inside src/services/{domain}Api
- Access checks use src/access/CanIAccess.tsx
- Client-specific shell comes from layout resolver
- Do not create client-specific page unless required

Expected output:

- page file
- related reusable components if needed
- service files if needed
- types if needed
- index.ts exports where useful

Example file placement:
src/pages/purchase/PurchaseOrderPage.tsx
src/components/tables/PurchaseOrderTable.tsx
src/services/purchaseApi/purchaseOrder.service.ts
src/services/purchaseApi/purchaseOrder.types.ts

---

## Template 2: Create Client Layout

Use when creating a client-specific layout/shell.

Inputs:

- client name/code
- layout purpose
- menu differences
- logo/branding requirements
- permission-based menu requirements

Rules:

- Layout goes inside src/clients/{client}/layout
- Theme goes inside src/clients/{client}/theme
- Config goes inside src/clients/{client}/config
- Do not place page business logic inside layout
- Do not place API calls inside layout
- Register layout in layout registry if project uses registry

Expected output:
src/clients/{client}/layout/{ClientName}Layout.tsx
src/clients/{client}/theme/{library}.theme.ts
src/clients/{client}/config/client.config.ts

---

## Template 3: Create API Service

Use when creating API integration.

Inputs:

- domain
- endpoint names
- request/response shape
- auth requirement
- RTK Query or normal service

Rules:

- API logic goes inside src/services/{domain}Api
- Types go near service
- Export through index.ts
- Do not put API calls inside pages/components
- Use existing base service from src/config/api if available

Expected output:
src/services/{domain}Api/{feature}.service.ts
src/services/{domain}Api/{feature}.types.ts
src/services/{domain}Api/index.ts

---

## Template 4: Create Redux Slice

Use when state is app/client/UI state.

Inputs:

- slice name
- state purpose
- actions
- selectors

Rules:

- Slice goes inside src/redux/slices
- Do not duplicate server response data unnecessarily
- Add to root reducer/store if required
- Export actions/selectors cleanly

Expected output:
src/redux/slices/{name}Slice.ts

---

## Template 5: Create Reusable Component

Use when creating a component used across multiple pages.

Inputs:

- component name
- category
- UI library
- props
- usage context

Rules:

- Component goes inside src/components/{category}
- No API calls inside component
- No tenant hardcoding
- Use theme tokens instead of hardcoded styles
- Export through index.ts where useful

Expected output:
src/components/{category}/{ComponentName}.tsx
src/components/{category}/index.ts

---

## Template 6: Create Utility

Use when creating pure helper logic.

Inputs:

- utility purpose
- input/output
- domain if any

Rules:

- Utility goes inside src/utils/{category}
- Must be pure when possible
- No React dependency
- No API calls
- No Redux usage

Expected output:
src/utils/{category}/{utilityName}.ts

---

## Template 7: Add Access Check

Use when protecting UI by permission.

Inputs:

- module
- action
- component/page area to protect

Rules:

- Use CanIAccess or existing access helper
- Do not hardcode role names directly in page JSX
- Keep permission constants/config inside src/access

Expected output:
Updated page/component using CanIAccess
Updated access config if needed

---

## Template 8: Add Client Theme

Use when adding or changing client-specific theme.

Inputs:

- client name/code
- UI library
- theme tokens
- branding rules

Rules:

- Theme file goes inside src/clients/{client}/theme
- Resolver/provider stays inside src/config/theme
- Do not hardcode colors inside components
- Update registry if project uses one

Expected output:
src/clients/{client}/theme/{library}.theme.ts or css
Updated theme registry if required

---

## Template 9: Add Client Config

Use when adding feature flags, labels, field visibility, or menu visibility.

Inputs:

- client name/code
- config purpose
- affected feature/page

Rules:

- Config goes inside src/clients/{client}/config
- Common resolver goes inside src/config if needed
- Do not use config for heavy business logic

Expected output:
src/clients/{client}/config/client.config.ts
Updated resolver if required

---

## Template 10: Modify Existing Feature

Use when changing an existing feature.

Rules:

- Search existing files first
- Prefer updating existing files over creating duplicates
- Keep file ownership intact
- Do not move files unless explicitly required
- Follow existing project patterns

Expected output:

- changed files
- reason for changes
- checklist result
