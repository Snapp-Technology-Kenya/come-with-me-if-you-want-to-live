# Infra Agent Instructions

- Read the repository-level specification index (`specification/spec-index.yaml`)
  and this layer's docs before touching code or automation.
- Keep this component's work queue in `infra/tasks.md`; update it before
  starting or finishing any task.
- Update PlantUML diagrams in `infra/model` before implementing structural
  changes and request approvals before committing spec/model updates.
- Use the provided makefiles/scripts for automation; add new tooling in
  `infra/scripts/` and keep it documented.
- Always test provisioning flows end-to-end (k3d up/down) before requesting
  review.