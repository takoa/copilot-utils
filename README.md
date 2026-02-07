# copilot-utils

A collection of prompts and custom agents for a better GitHub Copilot experience.

## Dependencies
- `memory`: required for Multi-Think. [[Stable]](vscode-insiders://settings/github.copilot.chat.copilotMemory.enabled) [[Insiders]](vscode-insiders://settings/github.copilot.chat.copilotMemory.enabled)

### Nice-to-Have Dependencies
- Web Search for Copilot: provides better research capabilities. [[Stable]](vscode:extension/ms-vscode.vscode-websearchforcopilot) [[Insiders]](vscode-insiders:extension/ms-vscode.vscode-websearchforcopilot)
- GitHub Pull Requests: provides PR information retrieval. [[Stable]](vscode:extension/GitHub.vscode-pull-request-github) [[Insiders]](vscode-insiders:extension/GitHub.vscode-pull-request-github)
- [GitHub CLI](https://cli.github.com/) (`gh`): an alternative to the `GitHub Pull Requests` extension.

## Usage
### Installation
### Global Installation
Copy the agents and prompts you want to use to:
- Windows:
    - Stable: `%APPDATA%\Code\User\prompts`
    - Insiders: `%APPDATA%\Code - Insiders\User\prompts`

Alternatively, you can use the Command Palette (`Ctrl+Shift+P`, `Cmd+Shift+P`, or `F1`) and select `New Custom Agent...` or `New Prompt File...`, then copy-paste the content.

### Workspace Installation
Copy the agents and prompts you want to use to `.github/agents/` and `.github/prompts/`, respectively.

## Agents

- **Orchestrator**: spawns and coordinates multiple subagents to plan, implement, review, and perform any other steps required to complete a task.
- **Review**: inspects diffs and produces triaged reports.
- **Multi-Think**: (*experimental*) runs multiple (default three) subagents independently, each with the same prompt, to increase the chances of producing a high-quality solution.
    - This may take a long time to complete.
    - This agent may not work as a subagent since currently subagents cannot spawn sub-subagents.

## Prompts

- **/merge-comment**: generates a comment suitable for squash-merging a pull request.
    - runs as `agent`.
- **/onboard**: generates or updates instruction files documenting dependencies, structure, workflows, and conventions in `/.instructions`, and adds references to them in `AGENTS.md` and `.gitignore`.
    - runs as `agent`.
    - creates the files if they do not exist.
