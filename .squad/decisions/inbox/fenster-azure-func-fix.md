# Decision: Azure Function samples require `main` field and build step

**By:** Fenster (Core Dev)
**Date:** 2026-03-06
**Context:** Brady hit "No job functions found" running the Azure Function sample

## Decision

All Azure Function samples (and any future serverless TypeScript samples) **must** include:

1. **`"main"` in package.json** pointing to the compiled JS entry point (e.g., `"main": "dist/functions/squad-prompt.js"`). Azure Functions v4 loads this file to discover `app.http()` registrations.
2. **`"start"` script** that builds before running: `"start": "npm run build && func start"`.
3. **README documentation** explaining why the build step is required.

## Why

Azure Functions runs JavaScript, not TypeScript. The v4 programming model discovers function registrations by loading the file specified in `main`. Without `main`, the runtime has nothing to load → silent failure → "No job functions found."

This is a common gotcha for TypeScript + Azure Functions v4. Documenting it in the sample prevents repeat debugging.

## Impact

- `samples/azure-function-squad/` — fixed
- Future serverless samples should follow this pattern
