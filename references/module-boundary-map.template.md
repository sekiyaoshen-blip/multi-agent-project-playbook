# Module Boundary Mapping

Use this worksheet before creating or reorganizing long-lived visible module tasks.

| Candidate Module | User Workflow | Owned Data | Owned Files / Components | External Interfaces | Dependencies | Risk Of Overlap |
|---|---|---|---|---|---|---|
| `<module>` | <workflow> | <data> | <files/components> | <API/schema/event/UI> | <dependency> | low / medium / high |

Rules:

- Prefer modules that own a user workflow, data boundary, or deployable component.
- Avoid modules that are merely task categories such as `frontend fixes` or `misc backend`.
- If two modules need to edit the same files often, either merge them or define explicit ownership rules.
- If a boundary is unclear, ask the main task to decide before creating a long-lived module task.
