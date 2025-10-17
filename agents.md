# Agent Configuration Tips

Practical advice for configuring local tooling and workflows when working with agent-style assistants such as Codex.

## Environment Setup
- Keep a dedicated workspace for experiments so destructive actions stay isolated from production repos.
- Version-control configuration files (`*.json`, `*.toml`) so you can diff agent prompt or tool changes over time.
- Store tokens in your shell keyring or environment manager instead of hard-coding them in config files.

## Prompting Workflow
- Start with a short, stable system prompt; iterate inside files instead of the chat when instructions become long.
- Prefer reproducible commands (scripts, `Makefile` targets) over ad-hoc instructions so agents can re-run workflows safely.
- Save good prompt/response pairs in a snippets file to seed future sessions quickly.

## Tooling Notes
- Use fast search tools (`rg`, `fd`) so the agent can retrieve context quickly without scanning entire repos.
- Teach the agent your project-specific lint/test commands early; reference them consistently to reinforce usage.
- Keep a scratchpad markdown file in the repo so the agent has a sanctioned place for notes and todos.
