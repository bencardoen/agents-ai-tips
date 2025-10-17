# ChatGPT Tips

Ideas for getting reliable output from ChatGPT (Plus / Enterprise).

## Prompt Craft
- Start with a short system prompt that states persona, constraints, and required style.
- Share a minimal working example when asking for code so the model can infer constraints.
- If the answer drifts, recap the last good state and restate the immediate objective.

## Session Management
- Use named custom instructions for recurring tasks (code reviews, release notes, etc.).
- Reset the conversation or open a new chat when the context window feels cluttered or contradictory.
- Export chats that contain critical reasoning steps and store them alongside project docs.

## Verification
- Ask for alternative implementations or test cases when the response is non-trivial.
- Run suggested commands locally before trusting them in automation or CI.
- When unsure, request citations or references and cross-check them manually.
