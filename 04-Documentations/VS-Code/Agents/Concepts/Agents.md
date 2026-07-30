#vscode 

## Subagents

When working on complex tasks, the main agent can delegate subtasks to subagents. A subagent is an independent AI agent that performs focused work, such as researching a topic or analyzing code, and reports the results back to the main agent.

The primary benefit of subagents is context optimization. Without subagents, every file read, search result, and intermediate step during research accumulates in the main agent's context window, potentially crowding out important information. Subagents perform their work in a separate context window and return only a summary, keeping the main conversation focused on the task at hand.

Key characteristics of subagents:

- **Context isolation**: each subagent runs in its own context window. It doesn't inherit the main agent's conversation history or instructions. It receives only the task prompt.
- **Synchronous execution**: the main agent waits for subagent results before continuing, because subagent findings typically inform the next step.
- **Parallel execution**: VS Code can spawn multiple subagents in parallel for tasks like analyzing security, performance, and accessibility simultaneously.
- **Focused results**: only the final result is returned to the main agent, keeping the main context focused and reducing token usage.

For example, the built-in [[Planning|Plan agent]] uses subagents to perform research and analysis before creating an implementation plan. Each subagent works autonomously and returns only its findings.

Learn more about using subagents.

## [Chat sessions](https://code.visualstudio.com/docs/agents/concepts/agents#_chat-sessions)

## Memory

Agents use memory to retain context across conversations. Rather than starting from scratch each session, agents recall your preferences, apply lessons from previous tasks, and build up knowledge about your codebase over time.

VS Code supports two complementary memory systems:

- **Memory tool**: a built-in tool that stores notes locally on your machine, organized in three scopes:
    - **User memory** (`/memories/`): persists across all workspaces and conversations. The first 200 lines are automatically loaded into every session.
    - **Repository memory** (`/memories/repo/`): scoped to the current workspace, persists across conversations.
    - **Session memory** (`/memories/session/`): scoped to the current conversation, cleared when it ends.
- **Copilot Memory**: a GitHub-hosted memory system that captures repository-specific insights across Copilot surfaces (coding agent, code review, CLI). Shared across GitHub Copilot beyond VS Code.

Learn more about [[Memory|memory in VS Code agents]]

## Planning

For complex tasks, jumping straight into code generation can lead to incomplete implementations or wrong architectural decisions. The built-in Plan agent collaborates with you to research the task and create a detailed implementation plan before any code changes are made. This ensures requirements are understood, edge cases are identified, and you agree on the approach before the agent starts writing code.

The plan agent uses a 4-phase iterative workflow:

1. **Discovery**: research the task using read-only tools and codebase analysis.
2. **Alignment**: ask clarifying questions to resolve ambiguities.
3. **Design**: draft a structured implementation plan.
4. **Refinement**: iterate on the plan based on your feedback.

The Plan agent does not make code changes until the plan is reviewed and approved. Once approved, you can hand off the plan to the default agent or save it for further refinement.

Learn more about [[Planning|planning with agents]].