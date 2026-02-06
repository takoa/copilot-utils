---
name: merge-comment
description: Generate squash merge comment for PR
agent: agent
---

Your goal is to generate a squash merge comment for the active pull request.

First, you MUST retrieve the diffs of the PR; the methods are ordered by priority, so try them in order:
1. Use #tool:github.vscode-pull-request-github/activePullRequest to get the pull request associated with the current branch, and obtain its diffs.
2. Use `gh` command to get the pull request associated with the current branch, and obtain its diffs.
3. Use `git` to identify the diffs between the current branch. If the base branch is not provided, use #tool:vscode/askQuestions to ask for it.`

Once you retrieve the diffs, you MUST deeply analyze them; then, generate a bulleted list summarizing the key changes made in the pull request, following the guidelines below:
- Make each item as short as possible, and keep it under 10 words at most.
- Group related changes into a single item when possible.
    - Good example: Add /new/path spec, implementation & tests
    - Bad example: Add /new/path spec; Add /new/path implementation; Add /new/path tests (in three bullets)
- Very small and trivial changes can be grouped together.
    - Example: Fix typos
- Do NOT include any opinions, just the facts.
- Do NOT include any emojis.
- Report the final merge comment in markdown format as a code snippet.
    - Surround the merge comment output with triple backticks (```).
    - The bullet sign MUST be `-` (followed by a space).
- Report anything noteworthy you find during the analysis as notes; do NOT mix them with the merge comment output.

To achieve the goal described above:
- You MUST plan the necessary steps using #tool:agent/runSubagent with the "Plan" agent and create a TODO list using #tool:todo .
    - Keep each TODO item focused; avoid combining multiple tasks into one item.
- You MUST execute every #tool:todo item using #tool:agent/runSubagent .
- You MUST NOT stop until the generation or updating is sufficiently completed.
- You MUST ask the user for clarifications using #tool:vscode/askQuestions when necessary or blocked.
- You MUST use #tool:web/fetch to understand any unfamiliar code, versions, frameworks, or libraries.
- You MUST avoid using `sed`, `python`, and any other tools with editing capabilities unless absolutely necessary.
- You NEVER create new files or modify existing files.
    - Use #tool:memory if you absolutely need to save temporary data.
