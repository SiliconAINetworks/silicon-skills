---
name: bridge-check
description: Use before declaring any feature, setting, button or endpoint "done". Traces the full chain from the user's action to the visible effect so no dead toggles, unconnected endpoints or settings that are saved but never read slip through.
---

# Bridge check

A feature is not done when the code compiles. It is done when the whole bridge carries weight from one bank to the other.

## The chain

Every user-facing feature is a chain. Walk it link by link and name the exact file and function for each:

1. **Trigger** – what the user does (click, toggle, form, schedule).
2. **Transport** – how it travels (event handler, request, route, message).
3. **Storage** – where it is written (database row, file, config, state).
4. **Reader** – who reads it back later (and *when*: on start, on every run, on reload).
5. **Effect** – what visibly changes because of it.

If any link has no name, the bridge is broken.

## Typical broken bridges

- A toggle that saves to the database, but the worker reads its config once at startup and never again.
- A new API route that exists on the server but is not in the allow-list or router table, so it returns 404 in production.
- A setting stored under one key and read under a slightly different one.
- A UI that shows "saved" because the request returned 200, while the handler silently ignored the field.
- A feature that works for new data but was never applied to records that already existed.

## How to check

- Perform the action for real (headless test, API call, or a throwaway test user), then read the storage, then trigger the reader, then observe the effect.
- Clean up every test record you created.
- If one platform has several clients (desktop, mobile, web), check the chain on each one that ships the feature.

## Output

When reporting done, list the five links with their concrete locations and say how each was verified. "Should work" is not a link.
