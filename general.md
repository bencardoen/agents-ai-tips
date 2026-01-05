# General Tips and Tricks


## Workflow tips
- If you use Codex in Agent mode, use a browser/chat alongside to help debug things interactively, prep next steps etc. This allows you to keep flow high.
- Crosscheck files between agents, let one agent generate the code, another the test cases.
- Instruct the agent to point the actual source code online if you doubt it's not using APIs correctly. Just looking up the URL can help it fix things.
- CGPT: Split conversations to keep context while working on separate parts (e.g. LaTeX vs code)

### Reproducibility 
- Share the chat so you have a permalink
- Feed in the stored chat in another chat to crosscheck and copy the full context
- Refactor generated code, and tell the agent to use pull requests, especially before and after major changes. 
- Tell it always to run tests on completion to show things work. 
- Before Agent Mode, use Chat Mode to review the workplan.
- For projects with code
    - Export conversations and agent logs in .md, in a separate directory so you can track brainstorming, code snippets etc. Permalinks may not be that permanent, backups are essential. 


### Troubleshooting
#### VSCode 
- Check that Sync isn't clobbering your local settings if you switch agents/authentication.



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
