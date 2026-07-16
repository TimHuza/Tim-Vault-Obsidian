#vscode-update

# Visual Studio Code 1.129

Show release notes after an update

---

_Release date: July 15, 2026_

---

Welcome to the 1.129 release of Visual Studio Code. This release brings a dedicated agent host, a new editor panel in the Agents window, running commands with `!`, and a preview of the modern UI.

- The agent host: Run agent sessions in a dedicated process and connect to them from multiple windows.

- New editor panel in the Agents window (Experimental): Review agent-generated files and diffs in a docked editor.

- Run commands with `!` prefix]: Run terminal commands directly from chat prompts.

- Modern UI preview (Experimental): Get a first look at the updated VS Code workbench appearance.

Happy Coding!

---

VS Code is rolling out gradually to all users. Use **Check for Updates** in VS Code to get the latest version immediately.

To try new features as soon as possible, [**download the nightly Insiders build**](https://code.visualstudio.com/insiders "https://code.visualstudio.com/insiders"), which includes the latest updates as soon as they are available.

---

In this update

- Agents
- Chat
- Editor experience
- Authentication
- Proposed API's
- Thank you

## Agents

### The agent host

We're rearchitecting how agent sessions work in VS Code around the agent host - a dedicated process that runs agent harnesses such as Copilot, Claude, and Codex, based on the Agent Host Protocol (AHP). Because a session lives in its own process, the same session can be connected to and rendered from multiple VS Code windows at once. The agent host's Copilot agent is powered by the Copilot SDK, which means that its behavior and functionality is aligned with the Copilot CLI, the standalone GitHub Copilot app, and other Copilot products.

We're actively developing the agent host and starting to roll it out to users in both the editor window and the [[Agents Window|Agents window]]. To opt in, enable   `[chat.agentHost.enabled](code-setting://chat.agentHost.enabled "View or change setting")` and then pick an agent host harness from the harness dropdown. The screenshot below shows how to select the `Copilot` harness on the agent host in the editor window:

![Screenshot showing the harness dropdown in the editor window.](https://code.visualstudio.com/raw/images/1_129/agent-host-harness-dropdown-editor.webp)

As we continue to invest in the agent host, some new features in these release notes may only be available when an agent runs on it. Those features link back to this section and, where relevant, note any additional settings that enable them (for example,   `[chat.agents.claude.preferAgentHost](code-setting://chat.agents.claude.preferAgentHost "View or change setting")` to enable the Claude agent on the agent host).

### New editor panel in the Agents window (Experimental)

The [[Agents Window|Agents window]] shows your conversation with an agent next to a detail area for the files and changes it produces. This release introduces a redesigned **editor panel** that brings the editor and the detail area together into one docked pane with a shared tab bar, so reviewing an agent's work feels like working in the main editor instead of switching between separate panels.

With the new editor panel, you can:

- Open files and diffs directly inside the docked editor, next to your chat, and add tabs with a **New Tab** action that matches the chat tab strip.
- Review changes in the **Changes** view with an improved diff experience: toggle between inline and side-by-side views, expand or collapse all files at once, and read changes in a more compact diff representation that fits more of the change on screen. The next action, such as **Create Pull Request**, is available right from the editor tab title, and editor keybindings like toggling the diff view work the same as they do in the main VS Code window.
- Pick up where you left off. Each session restores its side-pane width, open editors, active editor, and per-file collapsed state across session switches and window reloads.

This is an experimental, opt-in layout. To try it, enable `sessions.layout.singlePaneDetailPanel` and reload the window, since the setting is read once at startup.

### Session-management tools for Agent Host sessions

Agents running on the agent host (Copilot, Claude, and Codex) now have access to a suite of session-management tools, so an agent can enumerate, create, observe, and act on other sessions and chats without you needing to switch away from your current conversation.

With these tools, an agent can:

- List your sessions with their status, workspace, and changes, so it can find the right one to act on. Archived sessions are excluded unless explicitly requested.
- Read another session's recent conversation to understand what it's doing.
- Create a new session or a new chat within an existing session to hand off a sub-task, rather than overloading a single conversation with unrelated work.
- Send a message to a session or chat it created, to kick off or steer that work.

Whenever a tool creates or targets a session, VS Code renders an **Open Session** pill so you can jump straight to it. Sending a message to another session always asks for your confirmation first. An agent can't message its own chat, and a burst of sends is capped so a single request can't fan out into an unbounded number of sessions.

### Agents window improvements

This release includes several smaller improvements to the [[Agents Window|Agents window]] new-session flow:

- **Remembered new-session defaults**: the new-session picker remembers your last agent mode and approvals choices and uses them as the defaults the next time you create a session, so you don't have to reselect the same options for every task.
- **Worktree checkbox**: instead of choosing between folder and worktree isolation from a dropdown, the new-session configuration shows a single **New Worktree** checkbox. Check it to run the session with Git worktree isolation, which keeps the agent's changes in a separate folder until you're ready to review and merge them, or leave it unchecked to use folder isolation.

## Chat

### Run commands with `!` prefix

You can now prefix chat messages with a `!` to run their contents as terminal commands. This works in agent host sessions both in the editor and Agents window.

![Screenshot showing running a terminal command from chat with the ! prefix.](https://code.visualstudio.com/raw/images/1_129/bang-commands.webp)

### BYOK models with the Copilot agent harness

You can now use Bring Your Own Key (BYOK) models in the Agents window when you select the **Copilot** harness running on the agent host.

### Migrate prompt files to skills (Experimental)

Prompt files (`*.prompt.md`) are used to describe custom slash commands. They are only supported in the Local agent harness while other harnesses express slash commands with skills. For compatibility across harnesses, we recommend to migrate all prompt files to skills.

With   `[chat.customizations.promptMigration.enabled](code-setting://chat.customizations.promptMigration.enabled "View or change setting")` enabled, if you select a harness running on the the agent host and you have migratable prompt files, you'll now see a 'Migrate Prompts' entry in the AI Customizations overview.

The migration interface lets you:

- View prompt files from both workspace (`.github/prompts/`) and user data locations.
- Migrate selected files to skills and open the newly created skills.

![migrate prompt files](https://code.visualstudio.com/raw/images/1_129/migrate-prompt-files.webp)

## Editor experience

### Reopen an editor from the editor toolbar

When a file or diff supports multiple editors, you can switch editors directly from the editor toolbar. Open the **...** menu and select an editor from the **Reopen Editor With** submenu. This makes alternative editors easier to discover without using the Command Palette.

### Modern UI preview (Experimental)

**Setting**:   `[workbench.experimental.modernUI](code-setting://workbench.experimental.modernUI "View or change setting")`

You can now preview a modernized VS Code UI that updates the look and feel of the editor workbench. This is currently an experimental feature that you can enable with the   `[workbench.experimental.modernUI](code-setting://workbench.experimental.modernUI "View or change setting")` setting and is enabled by default in Insiders builds.

## Authentication

### GitHub Enterprise support for Copilot in the agent host

Developers whose GitHub Copilot access is provided through a GitHub Enterprise (GHE) instance can sign in and use Copilot in VS Code. Previously, the agent host's Copilot authentication only supported github.com, so a GHE-backed Copilot subscription could not complete sign-in: both the OAuth flow and the Copilot token request targeted github.com.

With this release, VS Code can authenticate Copilot against a GitHub Enterprise instance. When you sign in to Copilot, choose your GitHub Enterprise instance, and VS Code runs the sign-in flow and requests Copilot access tokens from that host instead of github.com. This works in both the editor window and the [[Agents Window|Agents window]], and with both the Copilot and Claude agents.

Because this support is part of the agent host, ensure the agent host is enabled with   `[chat.agentHost.enabled](code-setting://chat.agentHost.enabled "View or change setting")` .

## Proposed APIs

### Configure custom editors for diff and merge editors

Custom editors now opt out of diff and merge editors by default. As a result, a file can continue to open in a custom editor while its diffs and merges open in the built-in text editors. You might notice this change if you previously saw a custom editor when opening a diff or merge editor.

To open a diff in another editor, use the **Reopen Editor With** submenu in the editor toolbar. To always use a specific editor for matching diffs, configure the   `[workbench.diffEditorAssociations](code-setting://workbench.diffEditorAssociations "View or change setting")` setting.

The proposed `customEditorPriority` API provides separate priorities for files, diffs, and merge editors:

```json
"priority": {  "textEditor": "default",  "diffEditor": "option",  "mergeEditor": "never"}
```

The new `never` priority prevents automatic selection for that editor type while keeping the editor available for explicit selection.

If the text diff editor cannot display binary content, VS Code still falls back to a compatible custom diff editor.