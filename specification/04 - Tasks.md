  ---
  spec_order: 5
  required: true
  preceeded_by:
    - specification/03 - Processes.md
  references:
    - @specification/spec-index.yaml
    - @specification/workflow.yaml

  ---

  # Task list for project development.

  - Tasks are in priority order
  - The workflow for taking a task from this list is in AGENTS.MD
  - You may not read the task list without first reading all the top level specification files 00-03 in the specification folder in order.

  **Start by reading the full top-level specification in the specification folder**

  # Main Task list

  1. [ ] - Set up dev environment
    1. [ ] Create folders
    2. [ ] Add dummy files to empty folders
    3. [ ] Commit

  2. [ ] - Create infra 
      1. [ ] - Write k3d config
      2. [ ] - Write bash script that starts the server
      3. [ ] - Write makefile that kicks it all off, stops it, recycles it, etc.

  3. [ ] - Create Platform
      1. [ ] - Create nested folders for each platform feature
      2. [ ] - Install cert-manager and tekton first, using kustomize
      3. [ ] - Write tekton pipeline for istio
      4. [ ] - Write tekton pipeline for neon
      5. [ ] - Write tekton pipeline for redpanda

  4. [ ] - Create Server/API components
      1. [ ] - Write a basic express.js api server with bun with GET / and GET /health endpoints
      2. [ ] - Write a makefile that builds and runs the server in docker
      3. [ ] - Write a tekton pipeline that builds and deploys the server to k8s and tests it
      4. [ ] - write an istio ingress controller crd for the server

  5. [ ] - Create UI
      1. [ ] - Write a hello-world react app using the given stack
      2. [ ] - Write tekton ci/cd pipelines
      3. [ ] - Write an istio ingress controller crd for the ui
      4. [ ] - Test the UI through the server

  6. [ ] - Write documentation

  # Technical Debt Task List



  # REFERENCES

  @specification/spec-index.yaml
  @specification/workflow.yaml
