# copilot-utils

A collection of engineer-friendly, less invasive, model-agnostic prompts and custom agents for a better GitHub Copilot experience.

## Why?
This project aims to provide flexible, low-friction agents and prompts that better integrate into **your** workflows.

While there are many agents and prompts available for GitHub Copilot (and other agents), many impose their own methodologies: some optimized for specific models, some for fully automated coding, some demanding entirely new workflows, etc.

If you are engineering professionally, chances are you do not want those AI-centric changes. You want your agents to improve your established workflows. You want your agentic workflows, which you have already figured out on your own, to be enhanced. You do not want to throw everything away for something new while what you already have is working.

The agents and prompts in this project attempt to address these challenges while adding more value to GitHub Copilot.

## Dependencies
- `memory`: required by Multi-Think. [Stable](vscode-insiders://settings/github.copilot.chat.copilotMemory.enabled) [Insiders](vscode-insiders://settings/github.copilot.chat.copilotMemory.enabled)

### Recommended Dependencies
- Web Search for Copilot: provides better research capabilities. [Stable](vscode:extension/ms-vscode.vscode-websearchforcopilot) [Insiders](vscode-insiders:extension/ms-vscode.vscode-websearchforcopilot)
- GitHub Pull Requests: provides PR information retrieval. [Stable](vscode:extension/GitHub.vscode-pull-request-github) [Insiders](vscode-insiders:extension/GitHub.vscode-pull-request-github)
- [GitHub CLI](https://cli.github.com/) (`gh`): an alternative to the `GitHub Pull Requests` extension.

## Installation
### Agents
#### Global Installation
Copy the agent files you want to use to:
- Windows (WSL2 included):
    - Stable: `%APPDATA%\Code\User\prompts`
    - Insiders: `%APPDATA%\Code - Insiders\User\prompts`

Alternatively, you can use the Command Palette (`Ctrl+Shift+P`, `Cmd+Shift+P`, or `F1`) and select `New Custom Agent...`, then copy-paste the content.

#### Workspace Installation
Copy the agent files you want to use to `.github/agents/`.

### Prompts
#### Global Installation
Copy the prompt files you want to use to:
- Windows (WSL2 included):
    - Stable: `%APPDATA%\Code\User\prompts`
    - Insiders: `%APPDATA%\Code - Insiders\User\prompts`

Alternatively, you can use the Command Palette (`Ctrl+Shift+P`, `Cmd+Shift+P`, or `F1`) and select `New Prompt File...`, then copy-paste the content.

#### Workspace Installation
Copy the prompt files you want to use to `.github/prompts/`.

### Others
#### AGENTS.md
Copy this file to your repository without changing the file name.

## Abilities
### Agents

- **Orchestrator**: tackles the given task by researching, planning and delegating subtasks to appropriate subagents.
- **Review**: performs a thorough code review by inspecting diffs of the current branch and producing triaged reports.
    - *Note: This agent cannot run as a subagent because it is an "overkill" unless you specifically want a review.*
- **Multi-Think**: (*experimental*) executes multiple subagents (default: three) independently with the same prompt, then analyzes and synthesizes their outputs to produce a high-quality final result.
    - This process may be time-consuming if it fails to execute the subagents in parallel.
    - *Note: This agent cannot run as a subagent because subagents currently cannot spawn further subagents.*

### Prompts

- **/merge-comment**: generates a squash-merge commit message for the active pull request. No more default messages of commit titles!
- **/onboard**: generates or updates instruction files documenting dependencies, structure, workflows, and conventions in `/.instructions`, and adds references to them in `AGENTS.md` and `.gitignore`.
    - Creates the files if they do not exist.

### AGENTS.md
A template `AGENTS.md` file providing general requirements for development.
Please see [AGENTS.md](https://agents.md/) for basic usage.

## Notes
### Philosophy and Focus
The agents and prompts should be professionally useful.

We believe LLM is just another tool for engineers. We want to reduce the "boring" parts of engineering using LLMs while keeping the "fun" for humans.

Therefore, our priorities are:
- **Engineering Quality**: correctness, performance, security, maintainability, etc.
- **Flexibility**: to better fit into existing workflows.
- **Token/Prompt Efficiency**: to reduce cost and rate limits.

This also means the following are not our top priorities:
- Speed
- Reducing or eliminating human involvement
- Replacing existing workflows
