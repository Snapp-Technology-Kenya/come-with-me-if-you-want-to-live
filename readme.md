# Come With Me If You Want To Live

Examples of context driven development using hierarchical specifications, models, and task lists.

Because we are working with llm's, everything in this approach can be customized using your project's own ubiquitous language. I've called the spec folder 'specification' here, but you can call it whatever you like. In my professional life I'm lazy so I usually just call it 'spec'. I've seen many approaches, but stay consistent within a project.

# Initial development

When you start doing this yourself, your project specs won't be perfect. Use the llm to help you write the specs first. Add it as the first task in your task list.

# LLMs

- LLMs are idiot savants. They know everything and can do anything, but we need to constrain its creativity - channel it in the right direction.

## Terminology

- The 'query' we send to an llm is called a `prompt`.
- A prompt consists of sub-prompts - usually `system` and `user`.
  - A `user prompt` asks the llm to do something.
  - The `system prompt` tells the llm how to behave while doing it.
- A `coding agent` builds context (adds data to the user prompt) from files and tool outputs to help guide the llm down the right path.
- A `session` is a series of interactions with an llm that share a context. A conversation managed by the `coding agent`.
- `Context engineering` is the process of representing project architecture as a series of specifications formulated to take advantage of an LLM's capabilities

# LLM

- Stateless
- Sessions are managed by the agent, not the model
- The LLM can do anything, we reduce (constrain) its options

## Context

- LLMs work like humans - best not to overwhelm them with too much information at once.
- Remember, the agent will dynamically construct a context 
- Structured data is easier for an llm to understand than unstructured data
- If you can model it in plantuml or mermaid, do it

# MCP

- You should use mcp servers extensively
- VSCode itself provides tools to the agent in an mcp like way
- I use 
  - postgres mcp to research client's databases
  - kuberntes mcp to debug deployments
  - file mcp to read and write files in the project repo
  - trello mcp to manage project reporting
  - git mcp to manage version control
  - calculator for any calculations
  - context7 for manuals and documentation
  - jupyter mcp for data science tasks
- They provide a natural language interface to those tools and allow my agent to rapidly do research I would normally have to do manually

# Agentic Specification Driven Development

- Useful in all projects:
  - Removes a lot of repetitive work.
  - Stops LLMs from going off the rails.
  - Allows development of non-trivial applications.
  - Allows team collaboration.
  - Keeps track of progress so that work can be paused and resumed by different engineers.
- Define sub-agents for different parts of your project.
  - Allows monorepo development without overwhelming the llm
  - 

# State of the market

- You don't need extra extensions or tools to make this work in vscode
  - But, there are plenty of tools implementing this approach all aiming to make it easier and all getting it wrong
  - They all suffer from the same problem: way too much context at once
  - They all dumpt too much data into the context at once, confusing and disorienting the llm
  - They are improving all the time though and this mistake isn't that hard to fix
- Notable implementations include: 
  - VSCode with the Github Copilot extensions (my pick)
  - Claude Code
  - Most others are broken by design

# References

1. Anthropic: [Effective context engineering for AI agents](https://www.anthropic.com/index/effective-context-engineering-for-ai-agents)

Anthropic continue to lead the world in understanding what this technology is and how it works. If you're into this stuff, read all their papers.