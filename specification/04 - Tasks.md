  ---
  spec_order: 5
  required: true
  preceeded_by:
    - @specification/03 - Processes.md
  references:
    - @specification/spec-index.yaml

  ---

  # Task list for project development.

  - Tasks are in priority order
  - The workflow for taking a task from this list is in AGENTS.MD
  - You may not read the task list without first reading all the top level specification files 00-03 in the specification folder in order.

  **Start by reading the full top-level specification in the specification folder**

  # Main Task list

  1. [ ] - Create infra 
     1. [ ] Create folders and template files
     2. [ ] - Write k3d config
     3. [ ] - Write bash script that starts the server
     4. [ ] - Write makefile that kicks it all off, stops it, recycles it, etc.

  2. [ ] - Create Platform
     1. [ ] Create folders and template files
     2. [ ] - Create nested folders for each platform feature
     3. [ ] - Install cert-manager and tekton first, using kustomize
     4. [ ] - Write tekton pipeline for istio
     5. [ ] - Write tekton pipeline for postgres
     6. [ ] - Write tekton pipeline for redpanda

  3. [ ] - Create Server/API components
     1. [ ] Create folders and template files
     2. [ ] - Write a basic express.js api server with bun with GET / and GET /health endpoints
     3. [ ] - Write a makefile that builds and runs the server in docker
     4. [ ] - Write a tekton pipeline that builds and deploys the server to k8s and tests it
     5. [ ] - write an istio ingress controller crd for the server

  4. [ ] - Create UI
     1. [ ] Create folders and template files
     2. [ ] - Write a hello-world react app using the given stack
     3. [ ] - Write tekton ci/cd pipelines
     4. [ ] - Write an istio ingress controller crd for the ui
     5. [ ] - Test the UI through the server

  5.  [ ] - Write end-user documentation


  # Technical Debt Task List



  # REFERENCES

  @specification/spec-index.yaml
  @specification/workflow.yaml
