---
spec_order: 2
required: true
preceded_by:
  - @specification/00 - Specification.md
followed_by:
  - @specification/02 - Coding Standards.md
---

# Architecture

## Architectural overview 
This project has almost no PII concerns or consistency issues. The vast majority of work is on the read side and has no side-effect other than to the observability systems that track and log usage. This is a low volume system which will work up to maybe thousands of users at the most over a number of years. There might be spikes of about 30 users at once, then most of the time the system will remain idle. It is however still a critical commercial system and must be managed as such, hence the need for observability. Also, we will be taking payments and as we are providing an ai chatbot service to our users, there is a potential for misue which we must mitigate.

We use a monorepo with four basic layers - infra, platform, server, and ui. Infra is kubernetes (we use k3d for local dev). Platform contains tekton, cert-manager, istio, redpanda, neon, and other platform services. The server is custom components, api's and agents, all written in bun running in kubernetes, using the platform services and responding to requests from the UI. The server is domain driven, event driven, and cqrs based, but not event-sourced as such because we don't recreate objects from the bus - we read what we need from the db. The UI layer contains the user-interface in react+vite.

We follow a gitflow process with no human access to production servers, so full automation is required. It's ok to give imperative instructions in the terminal for debugging, etc., but all meaningful changes must be automated through scripts and pipelines.

## Component folder Structure

```
├── infra/ 
|   ├── spec/
|   ├── model/ 
|   ├── scripts/ 
|   ├── k3d-config.yaml 
|   ├── AGENTS.MD 
|   └── makefile 
├── platform/
|   ├── spec/
|   ├── model/ 
|   ├── services/ 
|   ├── AGENTS.MD 
|   └── makefile 
├─ server/
|   ├── spec/
|   ├── model/ 
|   ├── services/ 
|   |   ├── api/ 
|   |   ├── auth/ 
|   |   ├── student/
|   |   ├── teacher/
|   |   ├── analyst/
|   |   ├── admin/
|   ├── AGENTS.MD 
|   ├── pipeline.yaml 
|   ├── pipeline-run.yaml 
|   ├── kustomize.yaml
|   └── makefile 
├── ui/
|   ├── spec/
|   ├── model/ 
|   ├── scripts/ 
|   ├── AGENTS.MD 
|   └── makefile 
```

The services folder contains the domain driven components of the server. Each service gets a readme and an AGENTS.MD file, a spec folder and a model folder, along with a makefile and a tekton task definition yaml file.

## Stacks
**Infra**: K3D (K8s)
**Platform**: Tekton, Github+Gitea, cert-manager, Istio, Red Panda, Neon  
**Server**: Bun, Docker, Make, REST, MCP, Vercel AI-SDK  
**UI**: React, Vercel AI-SDK, Tanstack (Router/DB), ShadCN/UI, Vite, TailwindCSS

## Models
Use PlantUML to model system. Read models before changes; update diagrams to document changes. There should be a `models` folder in each layer of the stack containing at least a `main.puml` file with a component diagram as an overview of the layer.

# REFERENCES

@spec/00 - spec.md
@spec/01 - Architecture.md
@spec/02 - Coding Standards.md
@spec/03 - Processes.md
@spec/04 - Tasks.md
