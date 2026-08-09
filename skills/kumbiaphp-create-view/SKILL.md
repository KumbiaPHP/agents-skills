---
name: kumbiaphp-create-view
description: "Trigger: KumbiaPHP view, template, partial, .phtml. Create or modify views while preserving MVC separation and project conventions."
license: BSD-3-Clause
metadata:
  author: KumbiaPHP
  version: "1.0"
---

# Create a KumbiaPHP View

## Activation Contract

Use this skill when creating, modifying, or reviewing a KumbiaPHP view, shared template, or partial.

## Hard Rules

- Inspect the responsible controller action, nearby views, layouts, helpers, and shared templates before editing.
- Use `.phtml` files and follow the conventional `app/views/<controller>/<action>.phtml` location unless the target project establishes an override.
- Keep rendering and presentation decisions in views; keep persistence and business behavior out of templates.
- Reuse project layouts, helpers, components, and `views/_shared` partials when they already solve the need.
- Follow the project's output-escaping, accessibility, and localization conventions.
- Do not add frontend dependencies or abstractions without an explicit requirement.

## Decision Gates

| Situation | Action |
| --- | --- |
| Content belongs to one action | Keep it in that action's view. |
| Markup is already shared or clearly repeated | Reuse or minimally extend the established shared template or partial. |
| Required data is missing | Adjust the controller or model boundary instead of querying from the view. |

## Execution Steps

1. Trace the controller action to its expected view and inspect comparable templates.
2. Identify available data, layout, helpers, and shared presentation patterns.
3. Implement the smallest `.phtml` change with presentation-only logic.
4. Check affected links, forms, empty states, and rendered output using project conventions.
5. Run focused project checks and render or structurally inspect the affected page.

## Output Contract

Report changed files, controller/action mapping, reused layouts or partials, rendering checks, and any missing data contract or version-specific uncertainty.
