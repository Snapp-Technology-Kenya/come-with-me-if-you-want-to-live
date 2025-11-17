# Application Agent Instructions

- Read the repo-level spec index first, then the application-layer specs in `application/specification` before any change.
- Maintain the service task queue in `application/tasks.md` (add it if missing) and break work into small, testable subtasks.
- Keep PlantUML models in `application/specification/model`; update diagrams before modifying code or folder structure.
- Application services run on Bun; provide scripts/make targets so other layers can integrate quickly.
- Document new endpoints, agents, and data contracts in each service's README as you build them.
- Tests must run via `make test` (wire it up when implementing logic) before handing work off for review.
