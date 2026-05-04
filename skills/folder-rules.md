# Folder Rules

## Approved Source Structure

src/access
src/assets
src/clients
src/common
src/components
src/config
src/hooks
src/pages
src/redux
src/services
src/templates
src/utils
src/wrappers

Root files:
src/App.tsx
src/index.css
src/main.tsx
src/vite-env.d.ts

## Folder Ownership

### src/access

Use for:

- access management
- CanIAccess.tsx
- permission helpers
- access config
- role/action/module permission mapping

Allowed examples:

- src/access/CanIAccess.tsx
- src/access/access.types.ts
- src/access/access.config.ts
- src/access/index.ts

Do not place page logic here.

---

### src/assets

Use for:

- images
- icons
- fonts
- static files

Allowed examples:

- src/assets/images/logo.png
- src/assets/icons/search.svg

Do not place React components here.

---

### src/clients

Use for:

- client-specific layout
- client-specific theme
- client-specific config
- branding
- client-specific assets if required

Allowed examples:

- src/clients/default/layout/DefaultClientLayout.tsx
- src/clients/clientA/layout/ClientALayout.tsx
- src/clients/clientA/theme/antd.theme.ts
- src/clients/clientA/config/client.config.ts

Do not place common business logic here.
Do not place API services here.
Do not place Redux slices here.

---

### src/common

Use for:

- constants
- enums
- shared types
- shared validations
- shared static config not tied to client branding

Allowed examples:

- src/common/constants/app.constants.ts
- src/common/enums/status.enum.ts
- src/common/types/api-response.types.ts
- src/common/validations/phone.validation.ts

Do not place UI components here.

---

### src/components

Use for:

- reusable UI components used across pages
- reusable tables
- reusable forms
- reusable modals
- reusable buttons/wrappers around UI library components

Suggested subfolders:

- src/components/ui
- src/components/forms
- src/components/tables
- src/components/modals
- src/components/feedback
- src/components/navigation

Allowed examples:

- src/components/tables/PurchaseOrderTable.tsx
- src/components/forms/CustomerForm.tsx
- src/components/ui/AppButton.tsx

Do not place route-level pages here.
Do not place API calls here.
Do not place client-specific layout here.

---

### src/config

Use for:

- env config
- router config
- i18n config
- base service
- logout middleware
- app providers
- theme resolver
- layout resolver

Suggested subfolders:

- src/config/router
- src/config/theme
- src/config/api
- src/config/i18n

Allowed examples:

- src/config/env.config.ts
- src/config/router/AppRouter.tsx
- src/config/router/layoutResolver.tsx
- src/config/theme/themeResolver.ts
- src/config/api/baseService.ts
- src/config/api/logoutMiddleware.ts

Do not place business components here.

---

### src/hooks

Use for:

- reusable React hooks
- shared stateful logic

Allowed examples:

- src/hooks/useDebounce.ts
- src/hooks/useCurrentClient.ts
- src/hooks/usePagination.ts

Do not place page-specific one-time logic here unless it is reusable.

---

### src/pages

Use for:

- common route-level pages
- pages shared across clients by default

Allowed examples:

- src/pages/purchase/PurchaseOrderPage.tsx
- src/pages/customers/CustomerListPage.tsx
- src/pages/auth/LoginPage.tsx

Do not place reusable components here.
Do not place API service files here.
Do not place client-specific visual shell here.

---

### src/redux

Use for:

- Redux store
- root reducer
- slices
- middleware setup

Allowed examples:

- src/redux/store.ts
- src/redux/rootReducer.ts
- src/redux/slices/authSlice.ts
- src/redux/slices/sidebarSlice.ts

Use Redux for:

- auth state
- current client/org state
- UI state
- app state

Avoid Redux for:

- raw server response data when RTK Query or service cache can handle it

---

### src/services

Use for:

- API service logic
- RTK Query APIs
- request/response types
- domain-specific service modules

Suggested pattern:

- src/services/{domain}Api

Allowed examples:

- src/services/purchaseApi/purchaseOrder.service.ts
- src/services/purchaseApi/purchaseOrder.types.ts
- src/services/gstApi/gst.service.ts
- src/services/commonApi/common.service.ts

Do not put API calls inside pages or components.

---

### src/templates

Use for:

- invoice templates
- document templates
- printable templates
- PDF/HTML template components

Allowed examples:

- src/templates/invoices/DefaultInvoiceTemplate.tsx
- src/templates/invoices/GstInvoiceTemplate.tsx

Do not place normal pages here.

---

### src/utils

Use for:

- pure utility functions
- formatting
- parsing
- calculations
- mappers with no React dependency

Suggested subfolders:

- src/utils/date
- src/utils/number
- src/utils/string
- src/utils/file
- src/utils/formatters
- src/utils/mappers

Allowed examples:

- src/utils/date/formatDate.ts
- src/utils/number/formatCurrency.ts
- src/utils/string/toTitleCase.ts

Do not place hooks here.
Do not place React components here.
Do not place API calls here.

---

### src/wrappers

Use for:

- provider wrappers
- FormContext wrappers
- Lodash wrappers
- Auth wrappers
- third-party abstraction wrappers

Allowed examples:

- src/wrappers/form/FormProviderWrapper.tsx
- src/wrappers/auth/AuthGuard.tsx
- src/wrappers/lodash/safeGet.ts

Do not place business pages here.

## File Creation Rules

Before creating a file:

- identify ownership
- check whether a similar file already exists
- prefer updating existing module instead of duplicating
- create `index.ts` when the folder exposes reusable exports

## Forbidden Patterns

Bad:

- src/utils/helper.ts
- src/components/RandomComponent.tsx
- src/services/api.ts
- src/pages/components/Table.tsx
- src/clients/clientA/services/customerApi.ts

Good:

- src/utils/date/formatDate.ts
- src/components/tables/CustomerTable.tsx
- src/services/customerApi/customer.service.ts
- src/pages/customers/CustomerListPage.tsx
- src/clients/clientA/layout/ClientALayout.tsx
