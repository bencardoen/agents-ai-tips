# Git Hooks for AI Agent Workflows

Git hooks that enforce clean commit messages by blocking AI attribution markers and emojis.

## Why Use These Hooks?

AI coding assistants often add attribution footers to commits like:
```
🤖 Generated with [Claude Code](https://claude.com/claude-code)
Co-Authored-By: Claude <noreply@anthropic.com>
```

These markers:
- Violate minimal commit message conventions
- Add noise to git history
- Are often added without user consent
- Can trigger compliance or attribution issues

Note: If the commits are fully automated, then these hooks are not what you want. These hooks are useful in scenarios where agents commit but you reviewed/authored the code or you're instructing the agent to execute what you created. You should always comply with attribution rules (e.g. contribution.md, readme.md, ...)

## Available Hooks

### `prepare-commit-msg`
Runs before the commit message editor opens. Blocks commits with AI attribution patterns.

### `commit-msg`
Runs after the commit message is finalized. Final check for AI attribution patterns.

Both hooks check for:
- AI co-author tags (Claude, Copilot, GPT, etc.)
- "Generated with/by" patterns
- AI service names (Anthropic, OpenAI, GitHub Copilot, ChatGPT)

## Installation

### Option 1: Global Hooks (Recommended)

Apply these hooks to **all** your repositories:

```bash
# Create global hooks directory
mkdir -p ~/.config/git/hooks

# Copy the hooks
cp git-hooks/prepare-commit-msg ~/.config/git/hooks/
cp git-hooks/commit-msg ~/.config/git/hooks/

# Make them executable
chmod +x ~/.config/git/hooks/prepare-commit-msg
chmod +x ~/.config/git/hooks/commit-msg

# Configure git to use global hooks
git config --global core.hooksPath ~/.config/git/hooks
```

### Option 2: Per-Repository Hooks

Install hooks for a specific repository:

```bash
# Navigate to your repository
cd /path/to/your/repo

# Copy the hooks
cp /path/to/agents-ai-tips/git-hooks/* .git/hooks/

# Make them executable
chmod +x .git/hooks/prepare-commit-msg .git/hooks/commit-msg
```

## Testing

Test that the hooks work:

```bash
# Try to create a commit with AI attribution (this should fail)
git commit --allow-empty -m "Test commit

Co-Authored-By: Claude <noreply@anthropic.com>"

# Expected output:
# ERROR: Commit message contains forbidden AI attribution.
# Pattern matched: co-authored-by:.*claude
```

## Customizing Patterns

Edit the `PATTERNS` array in either hook to add or remove blocked patterns:

```bash
PATTERNS=(
  "co-authored-by:.*claude"
  "your-custom-pattern"
  # Add more patterns here
)
```

## Disabling Hooks Temporarily

If you need to bypass the hooks for a specific commit:

```bash
# Per-repository hooks
git commit --no-verify -m "Your message"

# Global hooks (temporarily override)
git -c core.hooksPath=/dev/null commit -m "Your message"
```

## Troubleshooting

**Hook not running:**
```bash
# Check if hooks are executable
ls -la ~/.config/git/hooks/

# Check git configuration
git config --get core.hooksPath
```

**Hook blocking legitimate commits:**
- Review the `PATTERNS` array and remove patterns you want to allow
- Or use `--no-verify` for specific commits (not recommended)
