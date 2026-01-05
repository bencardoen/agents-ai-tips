# Agent AI Tips & Tricks

Practical guides and tools for working with AI coding assistants (Claude, ChatGPT, Copilot, Perplexity, etc).

**NOTE**
Written from a Fedora 41 + VSCode + Julia/Python/Matlab perspective. PRs welcome!

## Quick Start

### Optional: Git Hooks
Prevent AI assistants from polluting your commit history with attribution markers:

(**Note**: You should still attribute commits and history, but for commits you review, hooks can be cleaner)

```bash
# Install global hooks (recommended)
mkdir -p ~/.config/git/hooks
cp git-hooks/* ~/.config/git/hooks/
chmod +x ~/.config/git/hooks/*
git config --global core.hooksPath ~/.config/git/hooks
```

See [git-hooks/README.md](git-hooks/README.md) for details.

## Contents

### Configuration & Tools
- **[git-hooks/](git-hooks/)** - Enforce clean commit messages, block AI attribution markers
- **[examples/](examples/)** - Ready-to-use config files for various tools and languages

### Guides
- **[agents.md](agents.md)** - Agent configuration (Codex, workspace setup, safety settings)
- **[general.md](general.md)** - Universal tips for all AI assistants
- **[ppx.md](ppx.md)** - Perplexity-specific advice
