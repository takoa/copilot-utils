# copilot-utils

A collection of engineer-friendly, less invasive, model-agnostic prompts and custom agents for a better GitHub Copilot experience.

You get:
- **Utility prompts and agents** designed for developers.
- **Flexible integration** that does not disrupt your existing workflow.

You don't get:
- *A complete LLM suite* entirely replacing your existing workflows.
- *Full automation*.

## Features

### Agents

| Agent            | Runs as Subagent | Description |
| :---             | :---             | :--- |
| **Orchestrate** | ✅              | Researches, plans, and delegates complex tasks to specialized subagents. |
| **Review**      | ❌              | Performs a comprehensive code review by inspecting diffs and generating triaged reports. |
| **Multi-Think** | ❌              | Runs multiple identical subagents in parallel to analyze a problem and synthesize a high-quality solution. |

### Prompts

| Prompt | Description |
| :--- | :--- |
| **/merge-comment** | Generates a concise, informative squash-merge commit message for your active PR. |
| **/onboard** | Creates or updates project documentation in `/.instructions` and configures `AGENTS.md`. |

### AGENTS.md
A template `AGENTS.md` file providing general requirements for development.
Please see [AGENTS.md](https://agents.md/) for basic usage.

## Prerequisites
Please open the URLs below to enable the necessary features in VS Code.

- **Custom Agents in Subagents**: 
    - Stable: `vscode://settings/chat.customAgentInSubagent.enabled`
    - Insiders: `vscode-insiders://settings/chat.customAgentInSubagent.enabled`
- **Memory for Agents**: used by Multi-Think.
    - Stable: `vscode://settings/github.copilot.chat.tools.memory.enabled`
    - Insiders: `vscode-insiders://settings/github.copilot.chat.tools.memory.enabled`

### Recommended Dependencies
- **GitHub MCP Server**: provides MCP access to pull requests.
    - Stable: `vscode://settings/github.copilot.chat.githubMcpServer.enabled`
    - Insiders: `vscode-insiders://settings/github.copilot.chat.githubMcpServer.enabled`
- **GitHub MCP Server (Lockdown)**
    - Stable: `vscode://settings/github.copilot.chat.githubMcpServer.lockdown`
    - Insiders: `vscode-insiders://settings/github.copilot.chat.githubMcpServer.lockdown`
- [**GitHub Pull Requests**](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github): an alternative to the GitHub MCP Server.
- [**GitHub CLI**](https://cli.github.com/) (`gh`): an alternative to the GitHub MCP Server.

## Installation

### Global Installation
To make agents and prompts available across all your projects, copy the agent files you want to use to:
- Windows (WSL2 included):
    - Stable: `%APPDATA%\Code\User\prompts`
    - Insiders: `%APPDATA%\Code - Insiders\User\prompts`

> Alternatively, you can use the Command Palette (`Ctrl+Shift+P`, `Cmd+Shift+P`, or `F1`) and select `New Custom Agent...`, then copy-paste the content.

### Workspace Installation
Use this method to share agents and prompts with your team for a specific project.

1. Create `.github/agents/` and `.github/prompts/` directories in your repository.
2. Copy the desired `.agent.md` and/or `.prompt.md` files into the appropriate directories.

## Notes
### Development
The development is mainly done with VS Code Insiders because many of the features used are actively being developed/experimented there.

### Known Issues
- **Insiders vs Stable**: some VS Code features may only be available in Insiders, or have different names in Stable.
    - **Tool Name Mismatches**: please update the tool names if you want to use the agents and prompts in Stable.

        | Name   | Stable         | Insiders              |
        | :---   | :---           | :---                  |
        | Memory | `#tool:memory` | `#tool:vscode/memory` |
- `Explorer` agent is disabled by default. It is because the agent is called as a subagent very often while its model is fixed to `Claude Haiku 4.5`, resulting in a high probability of affecting the overall quality of the parent agent.
    - This also automatically disables any other custom agents you added yourself. Please expand the `agents` field as needed.

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
