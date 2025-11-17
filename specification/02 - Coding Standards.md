---
spec_order: 3
required: true
preceded_by:
  - @specification/01 - Architecture.md
followed_by:
  - @specification/03 - Processes.md
---

# Project Coding Standards

---
applyTo: "**"
---
## General
- Write secure code at all times being aware of common vulnerabilities (e.g. OWASP Top 10)
- Consistent 2-space indentation, no tabs (except where required by syntax)
- Self-documenting code, but add comments to explain why, not what, and to keep notes for yourself
- Lowercase preferred (except where requried by syntax)
- Short methods, meaningful names
- Colored output, standard logging
- Never commit secrets, use .env where possible
- Always use lower-case file names except where it's illegal. e.g. readme.md, not README.md, and dockerfile, not Dockerfile
- Where not otherwise specified, follow the conventions of the language/framework being used
- Do not work on a file that is missing a coding standard block in this file. If you find such a file, add a task to write a coding standard block for it and get it approved and actioned before proceeding. Make a note for yourself so that you remember to proceed with the changes to the file after the coding standard block has been added and approved.

---
applyTo: "*.js, *.ts, *.jsx, *.tsx"
---
## JavaScript/TypeScript
- ES2024+: fat arrows, const/let, async/await, destructuring
- No braces for single-line conditionals
- Inline single-use variables
- Import order: external → internal → relative
- Interfaces over types for objects
- All source code in `src/`, tests in `tests/`

---
applyTo: "*.jsx, *.tsx"
---
## React
- Functional components + hooks only
- Tailwind, ShadCN/UI, Tanstack Router/DB
- Bun for dev server and tests

---
applyTo: "*.sh"
---
## Bash
- Modern bash, non-POSIX OK
- Full paths for tools (may be aliased): `/usr/bin/cat`

---
applyTo: "dockerfile"
---
## Dockerfile
- lowercase instructions, multi-stage builds

---
applyTo: "makefile"
---
## Makefile
- Use for build/automation
- Complex logic → bash scripts

---
applyTo: "*.puml"
---
## PlantUML
- Read the models before making changes
- Update diagrams before implementing *changes*

---
applyTo: "*.md"
---
## Markdown
- There are two types of markdown files - specification and documentation.
- Documentation is in readme.md files throughout the codebase.
- Specification markdown files are in the `specification/` folder.
- When writing specification files:
  - Put them at an appropriate level in the folder hierarchy
  - Keep things simple and concise
  - Compact the file through summarization where possible (whitespace isn't relevant)
  - Be direct, clear, and unambiguous
  - Issue orders
  - Use bullet points and lists where possible

---
applyTo: "*.yaml, *.yml"
---
## YAML
- 2-space indentation, no tabs
- Consistent quoting (single or double)
- Use anchors and references to avoid duplication

---