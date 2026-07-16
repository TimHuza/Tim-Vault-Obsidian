#vscode
## Permission levels

Permission levels are the high-level control for how much autonomy the agent has during a session. They sit on top of the finer-grained approval settings described in the rest of this article, such as tool approval, URL approval, and terminal command auto-approval.

Select a permission level from the permissions dropdown in the chat input area to choose how tool calls and approvals are handled.

The permission level applies to the current chat session, and can be changed at any time. New sessions start with the default permission level, which you can configure with the `chat.permissions.default` setting.

VS Code