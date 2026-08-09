---
name: kumbiaphp-create-model
description: "Trigger: KumbiaPHP model, ActiveRecord model. Create or modify models using the target project's database and persistence conventions."
license: BSD-3-Clause
metadata:
  author: KumbiaPHP
  version: "1.0"
---

# Create a KumbiaPHP Model

## Activation Contract

Use this skill when creating, modifying, or reviewing a KumbiaPHP model backed by ActiveRecord.

## Hard Rules

- Inspect comparable models, the database schema, and project configuration before editing.
- Extend `ActiveRecord` and follow the target project's database, table, file, class, and property naming conventions.
- Keep persistence behavior simple and colocated with the model when that matches existing practice.
- Use native validation and relationship mechanisms only after verifying their syntax for the installed KumbiaPHP version.
- Do not introduce repository abstractions, dependencies, or parallel persistence layers unless explicitly required.
- Keep changes compatible with PHP 8.0 unless the target repository states otherwise.

## Decision Gates

| Situation | Action |
| --- | --- |
| A comparable model exists | Reuse its verified ActiveRecord pattern. |
| Validation or relationships are needed | Check existing models, installed source, and current official documentation before declaring them. |
| The target is KumbiaPHP itself | Preserve public behavior and assess backward compatibility before changing conventions. |

## Execution Steps

1. Confirm the installed framework version, schema, and naming used by neighboring models.
2. Define only the fields, persistence behavior, validations, and relationships required by the task.
3. Implement the smallest native ActiveRecord model change.
4. Check controller and view consumers for assumptions affected by the model.
5. Run focused model or persistence checks against an appropriate test database or project harness.

## Output Contract

Report changed files, schema assumptions, conventions reused, validations or relationships added, checks run, and any version-sensitive decisions left unresolved.
