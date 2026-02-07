# copilot-utils

A collection of prompts and custom agents for better GitHub Copilot experience.

## Dependencies
- `memory`: required for Multi-Think. [[Stable]](vscode-insiders://settings/github.copilot.chat.copilotMemory.enabled) [[Insiders]](vscode-insiders://settings/github.copilot.chat.copilotMemory.enabled)

### Nice-to-Have Dependencies
- Web Search for Copilot: better research possibilities [[Stable]](vscode:extension/ms-vscode.vscode-websearchforcopilot) [[Insiders]](vscode-insiders:extension/ms-vscode.vscode-websearchforcopilot)
- GitHub Pull Requests VS Code extension: PR information retrieval [[Stable]](vscode:extension/GitHub.vscode-pull-request-github) [[Insiders]](vscode-insiders:extension/GitHub.vscode-pull-request-github)
- [GitHub CLI](https://cli.github.com/) (`gh`): CLI alternative if `GitHub Pull Requests VS Code extension` is not installed.

## Usage
### Installation
### Global Installation
Copy the agents and prompts you want to use to
- Windows:
    - Stable: `%APPDATA%\Code\User\prompts`
    - Insiders: `%APPDATA%\Code - Insiders\User\prompts`

Alternatively, you can use the command palette (`Ctrl+Shift+P` or `Cmd+Shift+P`, or `F1`) and select `New Custom Agent...` or `New Prompt File...` and copy-paste the content.

### Workspace Installation
Copy the agents and prompts you want to use to `.github/agents/` and `.github/prompts/` respectively.

## Agents

- **Orchestrator**: spawns and coordinates multiple subagents to plan, implement, review, and any other steps required to complete a task.
- **Review**: inspects diffs and produces triaged reports.
- **Multi-Think**: (*experimental*) runs multiple (default three) subagents with an identical prompt independently to increase the chance of producing a high-quality solution. 
    - This may take a long time to complete.
    - This agent may not work as a subagent since currently subagents cannot spawn sub-subagents.

## Prompts

- **/merge-comment**: generates a comment suited for squash merging a pull request.
    - runs as `agent`.
- **/onboard**: generate/update instruction files documenting dependencies, structure, workflows, and conventions in `/.instructions`, and add references to them in `AGENTS.md` and `.gitignore`.
    - runs as `agent`.
    - creates the files if they do not exist.
