---
name: onboard
description: Generate or update instruction files describing common project information
---

Generate or update instruction files that describe common information about the project.
The audience for the instruction files is other agents and human professionals who will work on the project in the future.

First:
1. You MUST identify and understand the dependencies of the project including the precise versions.
2. You MUST understand the project structure.
3. You MUST understand the commands, tools, and workflows used in the project.
4. You MUST understand the best practices and conventions followed in the project.

Then, you MUST organize and document the gathered information clearly, concisely and professionally:
1. `.instructions/dependencies.md` for additional dependency documentation.
    - Do NOT include information that is already well-documented in the package manager files, like imports and versions.
    - Focus on the core dependencies and adding well-organized, additional information on them, like covering five Ws (who, what, when, where, why).
2. `.instructions/structure.md` for project structure.
3. `.instructions/workflows.md` for commands and simple workflows.
4. `.instructions/conventions.md` for best practices and coding conventions.
5. For any other procedures that can be commonly used in the project but requires multiple steps, create a detailed instruction for each procedure.
    - Create as many instruction files as necessary.
    - Example A: `.instructions/how-to-add-endpoint.md` for a conventional way to add a new endpoint.
    - Example B: `.instructions/run-local.md` for how to run the project locally.

When documenting:
- You MUST create the necessary instruction files and directories if they do not exist.
- You MUST preserve the existing contents and structure as much as possible unless explicitly instructed otherwise.
- You MUST add newly found information.
- You MUST update outdated information.
- You MUST remove the contents that are no longer relevant.
- You MUST NOT include any "changelogs" and only focus on the current state of the project.

Also:
- You MUST create `/AGENTS.md` and `.gitignore` if they do not exist.
- You MUST update `/AGENTS.md` to refer to the instruction files as links with very short descriptions (up to 10 words).
- You MUST update `.gitignore` to ignore the `.instructions/` directory.

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
