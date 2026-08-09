# KumbiaPHP Agents and Skills

This repository provides focused, reusable instructions for agents working with KumbiaPHP. Its contents are vendor-neutral: they do not depend on a particular AI provider, coding agent, editor, or integration.

## Agents and Skills

| Concept | Role |
| --- | --- |
| Agent | A consumer or orchestrator that performs work and may load one or more skills. |
| Skill | A concrete instruction package for a reusable task, such as creating a controller or working with ActiveRecord. |

Skills are operational guidance, not broad framework tutorials. Each skill follows the [Agent Skills specification](https://agentskills.io/specification) and lives in its own directory with a required `SKILL.md` file. Agent implementations may be added separately in the future.

## Repository Layout

```text
.
├── README.md
└── skills/
    ├── kumbiaphp-create-controller/
    │   └── SKILL.md
    ├── kumbiaphp-create-model/
    │   └── SKILL.md
    ├── kumbiaphp-create-view/
    │   └── SKILL.md
    └── kumbiaphp-work-with-active-record/
        └── SKILL.md
```

## Skill Catalog

| Skill | Purpose |
| --- | --- |
| `kumbiaphp-create-controller` | Create or modify focused KumbiaPHP controllers and actions. |
| `kumbiaphp-create-model` | Create or modify models using project and ActiveRecord conventions. |
| `kumbiaphp-create-view` | Create or modify `.phtml` views while preserving MVC separation. |
| `kumbiaphp-work-with-active-record` | Perform persistence operations through KumbiaPHP ActiveRecord. |

## KumbiaPHP Approach

- Prefer KumbiaPHP-native functionality and the target project's established conventions.
- Apply KISS and DRY; avoid unnecessary layers, abstractions, and dependencies.
- Inspect the installed KumbiaPHP version and existing application before choosing version-sensitive APIs.
- Preserve MVC responsibilities and compatibility with PHP 8.0 unless the target repository states otherwise.
- Keep every skill independent of specific AI clients and integrations.

## Contributing

1. Scope a skill to one concrete, reusable task rather than a general documentation topic.
2. Create `skills/<skill-name>/SKILL.md`; use the same lowercase, hyphenated value for the directory and frontmatter `name`.
3. Write a concise frontmatter `description` that states what the skill does and when to use it.
4. Provide compact activation, constraints, workflow, verification, and reporting instructions.
5. Verify framework behavior against the target project's patterns, installed KumbiaPHP source, and current official documentation before naming APIs.
6. Prefer links to the relevant [KumbiaPHP documentation source](https://github.com/KumbiaPHP/Documentation) over copied tutorials. Summarize only the task-specific decision so guidance does not drift from the framework.
7. Do not add client configuration, integrations, generators, packages, or dependencies unless a separately scoped contribution requires them.
