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


## Preventing accidental destructive changes

### Codex/CGPT
#### Global
Global config is in ~/.codex/config.toml. 

Relevant settings:
```bash
# Auth (either works)
# preferred_auth_method = "chatgpt"
# preferred_auth_method = "apikey"  # Does not ? work with Codex Cloud 
# Auth is in ~/.codex


sandbox_mode = "workspace-write" # Write inside working repo/dir
approval_policy = "on-request"  # If unsafe, stop and ask

[sandbox_workspace_write] 
network_access = true  # This is needed if you expect to do package installs, or look up things. alternative, use environemnts.

[safety]  # Optional for very conservative use
dry_run = true
require_confirmation = true

[capabilities]
# restrict to non-execution, text-only suggestions
allow_shell = false
allow_file_write = true
allow_read_only = true
allow_execute = false

[filters]
# only engage on these file types
include_globs = ["**/*.md", "**/*.markdown"]
exclude_globs = ["**/*.sh", "**/*.bash", "**/*.zsh", "**/*.jl", "**/*.py", "**/*.js"]  # Very restrictive, but example
```

#### Per-project
Create AGENTS.MD in mixture of commands and instructions how to use package manager, what to ignore, and so on. 
See [examples/julia/AGENTS.md] for a Julia use case.