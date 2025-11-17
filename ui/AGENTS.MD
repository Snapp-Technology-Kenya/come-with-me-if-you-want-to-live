# UI Agent Instructions

- Read the repo specs and the UI-layer docs in `ui/specification` before touching code.
- Maintain UI tasks in `ui/tasks.md` and decompose features into bite-sized subtasks.
- Keep PlantUML diagrams up to date in `ui/specification/model` before changing the UI architecture.
- Build the SPA with React + Vite, TanStack, ShadCN, Tailwind, and Bun; expose common dev workflows through the makefile.
- Place scripts in `ui/scripts/` and keep `ui/src/` organized by feature; document conventions in `ui/readme.md`.
- Run lint/tests via Bun before handing off for review; record known issues alongside the tasks.
