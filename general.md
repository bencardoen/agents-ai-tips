# General Tips and Tricks

Quick reminders that apply no matter which assistant you are using.

## Stay Grounded
- Read the project README, `CONTRIBUTING`, and existing scripts before delegating work to an agent.
- Ask the agent to explain reasoning for non-trivial suggestions; prune steps that feel speculative.
- Track open questions in the chat so you can resolve them before merging changes.

## Validate Frequently
- Run existing tests or lightweight smoke checks after each significant edit.
- Prefer deterministic commands (`pytest`, `npm test`, `cargo check`) instead of ad-hoc scripts when possible.
- Capture command output highlights in commits or PR descriptions to document verification steps.

## Communicate Clearly
- Provide concrete file paths, commands, and acceptance criteria in your prompts.
- Note any local quirks (e.g., custom scripts, unusual tooling) so the agent can adapt quickly.
- Summarize outcomes and remaining tasks at the end of each session to maintain momentum.
