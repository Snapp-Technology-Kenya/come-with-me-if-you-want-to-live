---
spec_order: 1
required: true
preceded_by:
  - @specification/00 - Specification.md
followed_by:
  - @specification/02 - Coding Standards.md
---

# Architecture

## Architectural overview 
This project has almost no PII concerns or consistency issues. The vast majority of work is on the read side and has no side-effect other than to the observability systems that track and log usage. This is a low volume system which will work up to maybe thousands of users at the most over a number of years. There might be spikes of about 30 users at once, then most of the time the system will remain idle. It is however still a critical commercial system and must be managed as such, hence the need for observability. Also, we will be taking payments and as we are providing an ai chatbot service to our users, there is a potential for misue which we must mitigate.

We use a monorepo with four basic layers - infra, platform, server, and ui. Infra is kubernetes (we use k3d for local dev). Platform contains tekton, cert-manager, istio, redpanda, postgres, and other platform services. The server is custom components, api's and agents, all written in bun running in kubernetes, using the platform services and responding to requests from the UI. The server is domain driven, event driven, and cqrs based, but not event-sourced as such because we don't recreate objects from the bus - we read what we need from the db. The UI layer contains the user-interface in react+vite.

We follow a gitflow process with no human access to production servers, so full automation is required. It's ok to give imperative instructions in the terminal for debugging, etc., but all meaningful changes must be automated through scripts and pipelines.

## Component folder Structure

```
├── infra/ 
|   ├── specification/
|   |   ├── infra-spec.md
|   |   ├── infra-architecture.md
|   |   ├── infra-coding-standards.md
|   |   ├── infra-processes.md
|   |   ├── infra-tasks.md
|   |   ├── model/ 
|   |   |   ├── infra.puml
|   ├── scripts/ 
|   ├── k3d-config.yaml 
|   ├── AGENTS.MD 
|   └── makefile 
├── platform/
|   ├── scripts/ 
|   ├── specification/
|   |   ├── platform-spec.md
|   |   ├── platform-architecture.md
|   |   ├── platform-coding-standards.md
|   |   ├── platform-processes.md
|   |   ├── platform-tasks.md
|   |   ├── platform-notes.md
|   |   ├── model/ 
|   |   |   ├── platform.puml
|   ├── services/ # We don't need separate models for platform services as they're all standard components
|   |   ├── cert-manager/
|   |   |   ├── specification/. 
|   |   |   |   ├── cert-manager-spec.md
|   |   |   ├── kustomize.yaml
|   |   |   ├── cert-manager.yaml
|   |   |   ├── namespace.yaml
|   |   ├── redpanda/
|   |   |   ├── specification/
|   |   |   |   ├── red-panda-spec.md
|   |   |   ├── kustomize.yaml
|   |   |   ├── kustomize.yaml
|   |   |   ├── namespace.yaml
|   |   ├── istio/
|   |   |   ├── specification/
|   |   |   |   ├── istio-spec.md
|   |   |   ├── kustomize.yaml
|   |   |   ├── istio.yaml
|   |   |   ├── namespace.yaml
|   |   ├── postgres/
|   |   |   ├── specification/
|   |   |   |   ├── postgres-spec.md
|   |   |   ├── kustomize.yaml
|   |   |   ├── postgres.yaml
|   |   |   ├── namespace.yaml
|   ├── AGENTS.MD 
|   └── makefile 
|   └── kustomize.yaml 
├─ application/
|   ├── specification/
|   |   ├── application-spec.md 
|   |   ├── application-architecture.md 
|   |   ├── application-coding-standards.md 
|   |   ├── application-processes.md 
|   |   ├── application-tasks.md
|   |   ├── application-notes.md
|   |   ├── model/ 
|   |   |   ├── application.puml
|   ├── services/ 
|   |   ├── api/
|   |   |   ├── chat/ 
|   |   |   |   ├── specification/
|   |   |   |   |   ├── chat-spec.md 
|   |   |   |   ├── model/ 
|   |   |   |   |   ├── chat.puml
|   |   |   |   ├── src/ 
|   |   |   |   ├── package.json 
|   |   |   ├── payments/ 
|   |   |   |   ├── specification/
|   |   |   |   |   ├── payments-spec.md 
|   |   |   |   ├── model/ 
|   |   |   |   |   ├── payments.puml
|   |   |   |   ├── src/ 
|   |   |   |   ├── package.json 
|   |   |   ├── users/
|   |   |   |   ├── specification/
|   |   |   |   |   ├── users-spec.md 
|   |   |   |   ├── model/ 
|   |   |   |   |   ├── users.puml
|   |   |   |   ├── src/ 
|   |   |   |   ├── package.json 
|   |   ├── auth/ 
|   |   |   ├── specification/
|   |   |   |   ├── auth-spec.md 
|   |   |   ├── model/ 
|   |   |   |   ├── auth.puml
|   |   |   ├── src/ 
|   |   |   ├── package.json 
|   |   ├── admin/
|   |   |   ├── specification/
|   |   |   |   ├── admin-spec.md 
|   |   |   ├── model/ 
|   |   |   |   ├── admin.puml
|   |   |   ├── src/ 
|   |   |   ├── package.json 
|   ├── AGENTS.MD 
|   ├── pipeline.yaml 
|   ├── pipeline-run.yaml 
|   ├── kustomize.yaml
|   └── makefile 
├── ui/
|   ├── specification/
|   |   ├── model/ 
|   |   |   ├── ui.puml
|   |   ├─- ui-spec.md
|   |   ├─- ui-architecture.md
|   |   ├─- ui-coding standards.md
|   |   ├─- ui-processes.md
|   |   ├─- ui-tasks.md
|   |   ├─- ui-notes.md
|   ├── scripts/ 
|   ├── src/ 
|   ├── AGENTS.MD 
|   └── makefile 
|   └── package.json 
```

- These folders describe a pattern that should be followed for any new component added to the system.
- The services folder contains the domain driven components of the server. Each service gets a readme and an AGENTS.MD file, a spec folder and a model folder, along with a makefile and a tekton task definition yaml file.

## Stacks
- **Infra**: K3D (K8s)
- **Platform**: Tekton, Github+Gitea, cert-manager, Istio, Red Panda, Postgres. - rest, ddd, cqrs, event-driven (but not event-sourced)
- **Application**: Bun, Docker, REST, MCP, Vercel AI-SDK  
- **UI**: React SPA, Tanstack (Router/DB), ShadCN/UI, Vite, TailwindCSS

## Models
- Use PlantUML to model system. Read models before changes; update diagrams to document changes. 
- There must be a `models` folder in each layer of the stack containing at least a `main.puml` file with a component diagram as an overview of the layer.

# REFERENCES

- @infra/specification/infra-spec-index.yaml
- @platform/specification/platform-spec-index.yaml
- @application/specification/application-spec-index.yaml
- @ui/specification/ui-spec-index.yaml