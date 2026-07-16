#vscode
## Built-in agents

Local agent sessions use one of three built-in agents, each optimized for different types of tasks. You can switch between agents at any time during a chat session by selecting a different agent from the agent picker in the Chat view. For more specialized workflows, you can create your own [custom agents](https://code.visualstudio.com/docs/agent-customization/custom-agents).

### Agent

Agent is optimized for complex coding tasks based on high-level requirements that might require running terminal commands and tools. The AI operates autonomously, determining the relevant context and files to edit, planning the work needed, and iterating to resolve problems as they arise.

VS Code directly applies code changes in the editor, and the editor overlay controls enable you to navigate between the suggested edits and review them. The agent might invoke multiple [tools](https://code.visualstudio.com/docs/chat/chat-tools) to accomplish different tasks.

You can [customize chat with extra tools](https://code.visualstudio.com/docs/chat/chat-tools) by adding MCP servers or installing extensions that contribute tools.