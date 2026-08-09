---
name: kumbiaphp-work-with-active-record
description: "Trigger: KumbiaPHP ActiveRecord, query, pagination, aggregate, save, update, delete. Use native persistence APIs safely and consistently."
license: BSD-3-Clause
metadata:
  author: KumbiaPHP
  version: "1.0"
---

# Work with KumbiaPHP ActiveRecord

## Activation Contract

Use this skill for KumbiaPHP ActiveRecord queries, pagination, aggregates, writes, validation, or relationships.

## Hard Rules

- Confirm the model extends classic framework `ActiveRecord`/`KumbiaActiveRecord`; inspect `LiteRecord`, other packages, overrides, and conditional categories below.
- Use the Stable Core directly for routine work. Never import Laravel, Doctrine, or generic ORM assumptions.
- Prefer native ActiveRecord and selection methods over wrappers, dependencies, duplicated persistence logic, or manual SQL.
- Allowlist externally writable fields; never persist an unfiltered request payload.
- Keep destructive scope explicit and verify atomicity for multi-record writes.
- Keep PHP 8.0 compatibility unless the target repository specifies otherwise.

## Decision Gates

### Stable Core API

| Need | Use directly |
| --- | --- |
| Select | `find($id): model|false`; `find(...options): model[]`; `find_first(...options): model|false`; `exists($idOrCondition): COUNT scalar` (test truthiness); `find_all_by($field, $value): model[]`; `distinct($column, ...options): array`. |
| Query options | Pass named strings such as `"conditions: ..."`, `"order: ..."`, `"limit: N"`, `"offset: N"`, `"columns: ..."`, `"distinct: ..."`, `"group: ..."`, `"having: ..."`, or `"join: ..."`. No-argument `find()` returns all rows; no matches return `[]`. |
| Paginate | `paginate(...options, "page: N", "per_page: N")` defaults to 1/10 and returns an object with `items`, `current`, `next`, `prev`, `total`, `count`, and `per_page`; require positive integers. |
| Aggregate | `count(...options)`, `sum($column, ...options)`, `average(...)`, `maximum(...)`, and `minimum(...)` return database scalars. |
| Write | `create($fields)` inserts; `save($fields)` inserts or updates by existence; `update($fields)` requires an existing row; `delete($idOrCondition)` or loaded `delete()` removes matches. Test results for truthiness, not strict booleans. |
| Validation | `save()` and delegated writes return falsey on metadata/configured validation, callback cancellation, or database failure; validation reports through `Flash::error`. |

`conditions`, `join`, and `having` are SQL fragments, not bindings. Keep fragments static or allowlisted; handle external values only with a verified safe project pattern.

### Inspect Before Use

| Category | Verify |
| --- | --- |
| Version or extension | Installed source for overrides, alternate packages, plugins, or custom bases. |
| Validation or callbacks | Declarations, messages, order, cancellation, and side effects. |
| Relationships | Declared names, keys, cardinality, loading, and multi-connection behavior. |
| Transactions or bulk writes | Driver/project pattern, rollback, partial failure, and scope. |
| Raw SQL or schema | Binding/quoting, columns, keys, defaults, timestamps, views, and database behavior. |

## Execution Steps

1. Confirm the model family, operation scope, and external-data trust boundary.
2. Choose the smallest Stable Core method; inspect only when a conditional category applies.
3. Allowlist writable fields and dynamic query fragments before persistence.
4. Verify result shape, falsey failure, page boundaries, and unrelated-row preservation.

## Output Contract

Report operation, scope, stable methods, allowed external fields/fragments, files, inspected conditions, checks, compatibility, and unresolved API details.
