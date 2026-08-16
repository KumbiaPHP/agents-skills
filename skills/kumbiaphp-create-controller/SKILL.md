---
name: kumbiaphp-create-controller
description: "Trigger: KumbiaPHP controller, action, route. Create or modify controllers while preserving the target application's MVC conventions."
license: BSD-3-Clause
metadata:
  author: KumbiaPHP
  version: "1.0"
---

# Create a KumbiaPHP Controller

## Activation Contract

Use this skill when creating, modifying, or reviewing a KumbiaPHP controller or action, including work that affects its route or rendered view.

## Hard Rules

- Inspect nearby controllers, the application controller hierarchy, routes, and related views before editing.
- Follow the established `AppController` hierarchy, file naming, class naming, and action conventions.
- Keep controllers focused on request coordination. Put persistence and domain behavior in the appropriate model.
- Prefer native KumbiaPHP behavior; do not add architectural layers or dependencies without an explicit project requirement.
- Keep changes compatible with PHP 8.0 unless the target repository requires another version.
- Verify version-sensitive behavior in the installed framework source or current official documentation; do not guess API names.

## Decision Gates

| Situation | Action |
| --- | --- |
| A matching controller exists | Extend its established pattern with the smallest change. |
| An action renders a view | Confirm the conventional controller/action `.phtml` path or the project's explicit override. |
| Routing differs from convention | Inspect route configuration before changing either side. |

## Execution Steps

1. Identify the installed KumbiaPHP version and inspect comparable controllers.
2. Define the action's request, response, route, model, and view responsibilities.
3. Implement the smallest controller change using the existing base controller and framework facilities.
4. Align related routes and views only when the requested behavior requires it.
5. Run focused project checks and exercise or structurally verify the affected action path.

## Output Contract

Report changed files, reused conventions, affected routes or views, validation performed, and any unresolved version-specific behavior.
