---
name: merge-comment
description: Generate squash-merge comment for active PR
---

Generate a squash merge comment for the active pull request (associated with the current branch).

First, you MUST retrieve the diffs of the active pull request; attempt the following methods in order of priority:

1. Use #tool:github/* to get the active pull request and obtain its final diffs.
2. Use `gh` command to get the active pull request and obtain its final diffs.
3. Use `git` to identify the diffs between the current branch and its base branch. If the base branch is not provided, use #tool:vscode/askQuestions to ask for it.

You MUST focus on the final diffs of the active pull request, not on all changes made in the branch (like intermediate commits or local uncommitted changes).

Once you have retrieved the final diffs, you MUST thoroughly analyze them. Then, generate a summary as a bulleted list following the guidelines below:
- Keep items as short as possible and strictly under 10 words.
    - Prefer common words (like "add", "update", "edit", etc.) and common signs ("+", "-", etc.)
- Keep the number of items minimal while covering all significant changes.
- Group related changes into a single item when possible.
    - Good example: Add /new/path spec, implementation & tests
    - Bad example: Add /new/path spec; Add /new/path implementation; Add /new/path tests (in three bullets)
- Very small and trivial changes can be grouped together.
    - Example: Fix typos
- State facts only; omit opinions.
- Do NOT use any emojis.
- Do NOT include anything other than the final diffs of the active pull request.
- Report the final merge comment in Markdown format as a code snippet.
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
    - Unless explicitly provided, you should use your own knowledge to determine or construct URLs.
    - Try to use authoritative documents.
- You MUST avoid using `sed`, `python`, and any other tools with editing capabilities unless absolutely necessary.
- You NEVER create new files or modify existing files.
    - Use #tool:vscode/memory if you absolutely need to save temporary data.
