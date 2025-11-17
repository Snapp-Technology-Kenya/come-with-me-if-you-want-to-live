# Platform Agent Instructions

- Read the global specs and `platform/specification` docs before starting work.
- Track platform-specific tasks in `platform/tasks.md`; do not pick up a task without updating the list.
- Keep Tekton, Istio, Postgres, Redpanda, and cert-manager assets under `platform/services/<service>`.
- Update PlantUML component diagrams in `platform/specification/model` before modifying services and request approval for spec/model changes.
- Use `platform/scripts/` for operational helpers and surface them through the layer makefile.
- Every change must be tested through kustomize/tekton manifests before review; document known limitations in service READMEs.
