# AGENTS.md — SpatialGraphs.jl

## Scope & Safety
- Operate **only inside this repository**.
- **Never** modify files outside this workspace. If an action requires leaving, **ask me first**.
- Avoid destructive commands (e.g., `rm -rf`, `chown -R`, writing into `$HOME`) unless I explicitly approve.

## Julia setup
- Preferred toolchain: `juliaup` (install or update if missing).
- Default Julia: `1.11` (use `julia +1.11`).
- Activate the package environment in repo root before any Julia code:
  ```bash
  julia +1.11 -e 'using Pkg; Pkg.activate("."); Pkg.instantiate()'
  ```

## Common commands
- **Format**:
  ```bash
  julia +1.11 -e 'using Pkg; Pkg.activate("."); using JuliaFormatter; format(".")'
  ```
- **Tests**:
  ```bash
  julia +1.11 -e 'using Pkg; Pkg.activate("."); Pkg.test()'
  ```
- **Docs** (if present):
  ```bash
  julia +1.11 -e 'using Pkg; Pkg.activate("docs"); Pkg.instantiate(); include("docs/make.jl")'
  ```

## Conventions
- Keep `src/` clean; avoid global state.
- Add/modify unit tests under `test/` for each change.
- Use `Project.toml`/`Manifest.toml`; don’t write outside the repo.
