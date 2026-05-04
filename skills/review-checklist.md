# Review Checklist

Before final response for any frontend development task, verify all checks.

## Folder Structure

- Did every new file go into an approved folder?
- Did the file owner make sense?
- Were random folders avoided?
- Were broad dumping folders avoided?
- Were `index.ts` exports added where useful?

Result:
PASS / FAIL

## Pages

- Are common pages inside src/pages?
- Were client-specific pages avoided unless truly needed?
- Is the page free from hardcoded client checks?
- Is routing/layout handled outside page where appropriate?

Result:
PASS / FAIL

## Components

- Are reusable components inside src/components?
- Are page-specific components kept close only if project allows it?
- Are components free from API calls?
- Are components free from tenant hardcoding?
- Is the selected UI library used consistently?

Result:
PASS / FAIL

## Multi-client

- Are client-specific layouts inside src/clients/{client}/layout?
- Are client-specific themes inside src/clients/{client}/theme?
- Are client-specific configs inside src/clients/{client}/config?
- Is business logic kept out of client layout?
- Is default fallback preserved where registry/resolver is used?

Result:
PASS / FAIL

## Theme

- Are theme tokens/config used instead of hardcoded styles?
- Are client colors not hardcoded inside components?
- Is theme resolver/provider respected?
- Is selected UI library theme system used correctly?

Result:
PASS / FAIL

## Access

- Is CanIAccess or access helper used?
- Are role checks not hardcoded directly in JSX?
- Are module/action names consistent?
- Is access config updated if needed?

Result:
PASS / FAIL

## Services/API

- Are API calls inside src/services/{domain}Api?
- Are request/response types placed correctly?
- Is base service reused if available?
- Are API calls avoided inside pages/components?

Result:
PASS / FAIL

## Redux

- Are slices inside src/redux/slices?
- Is Redux used only for app/client/UI state?
- Is server data duplication avoided?
- Was root reducer/store updated if required?

Result:
PASS / FAIL

## TypeScript

- Is `any` avoided?
- Are props typed?
- Are API responses typed?
- Are utility inputs/outputs typed?
- Are imports clean?

Result:
PASS / FAIL

## UI Library

- Was the selected UI library followed?
- Were AntD/MUI/Shadcn not mixed?
- Were official docs/skills used when UI API was uncertain?
- Were deprecated/guessed props avoided?

Result:
PASS / FAIL

## Final Output Must Include

The final response must include:

1. Files created/changed
2. Final file tree
3. Why each file belongs there
4. Assumptions
5. Checklist result

## Failure Rule

If any checklist item fails:

- state the failure clearly
- explain what must be fixed
- do not pretend the task is complete
