#vscode-update 


# Visual Studio Code 1.136

Show release notes after an update

Follow us on [LinkedIn](https://www.linkedin.com/showcase/vs-code "https://www.linkedin.com/showcase/vs-code"), [X](https://go.microsoft.com/fwlink/?LinkID=533687 "https://go.microsoft.com/fwlink/?LinkID=533687"), [Bluesky](https://bsky.app/profile/vscode.dev "https://bsky.app/profile/vscode.dev"), [Instagram](https://www.instagram.com/vscode.ig "https://www.instagram.com/vscode.ig") | [View online](https://code.visualstudio.com/updates "https://code.visualstudio.com/updates")

---

_Release date: September 2, 2026_

**Update 1.136.1**: The update addresses these [issues](https://github.com/microsoft/vscode/pulls?q=is%3Apr+milestone%3A1.136.1+is%3Aclosed+label%3Acandidate "https://github.com/microsoft/vscode/pulls?q=is%3Apr+milestone%3A1.136.1+is%3Aclosed+label%3Acandidate").

---

Welcome to the 1.136 release of Visual Studio Code. This release helps you finish pull requests with agents and manage agent work across complex workspaces and related chats.

- [Agent Merge (Preview)](https://code.visualstudio.com/raw/#agent-merge-preview "#agent-merge-preview"): Resolve review feedback, failed checks, and merge conflicts until your pull request is ready to merge.
    
- [Multi-root workspaces (Experimental)](https://code.visualstudio.com/raw/#multi-root-workspaces-in-editor-window-experimental "#multi-root-workspaces-in-editor-window-experimental"): Work with Copilot and Claude agent sessions across all folders in a multi-root workspace.
    
- [Chat backgrounds (Experimental)](https://code.visualstudio.com/raw/#chat-backgrounds-in-the-agents-window-experimental "#chat-backgrounds-in-the-agents-window-experimental"): Personalize the Agents window with built-in patterns or your own images.
    
- [Chat sessions](https://code.visualstudio.com/raw/#navigate-related-chats-and-sessions "#navigate-related-chats-and-sessions"): Organize related chats in a session hierarchy and quickly see which ones need your attention.
    

Happy Coding!

---

VS Code is rolling out gradually to all users. Use **Check for Updates** in VS Code to get the latest version immediately.

To try new features as soon as possible, [**download the nightly Insiders build**](https://code.visualstudio.com/insiders "https://code.visualstudio.com/insiders"), which includes the latest updates as soon as they are available.

---

In this update

- [[September 2, 2026 VS Code Update#The Story of VS Code World Premiere|The Story of VS Code: World Premiere]]
- [[September 2, 2026 VS Code Update#Agents|Agents]]
- [[September 2, 2026 VS Code Update#Chat|Chat]]
- [[September 2, 2026 VS Code Update#Accessibility|Accessibility]]
- [[September 2, 2026 VS Code Update#Editor experience|Editor experience]]
- [[September 2, 2026 VS Code Update#Code editing|Code editing]]
- [[September 2, 2026 VS Code Update#Integrated browser|Integrated browser]]
- [[September 2, 2026 VS Code Update#Terminal|Terminal]]
- [[September 2, 2026 VS Code Update#Deprecated features and settings|Deprecated features and settings]]
- [[September 2, 2026 VS Code Update#Thank you|Thank you]]

## The Story of VS Code: World Premiere

Discover the story behind VS Code, from its early beginnings to the platform millions of developers use today, and the community that helped shape it along the way.

**[Premiere: September 4 at 8:00 AM PT. Join us!](https://aka.ms/the-story-of-vs-code "https://aka.ms/the-story-of-vs-code")**

[![Graphic poster featuring the VS Code logo glowing over a dark background filled with programming code, with the title "The Story of VS Code."](https://code.visualstudio.com/raw/images/1_136/the-story-of-vs-code.png)](https://aka.ms/vscode-trailer "https://aka.ms/vscode-trailer")

## Agents

### Multi-root workspaces in editor window (Experimental)

**Settings**: `chat.agentHost.copilotAgent.multiRootEnabled`, `chat.agentHost.claudeAgent.multiRootEnabled`

Copilot and Claude agent sessions in the editor window Chat view support [multi-root workspaces](https://code.visualstudio.com/docs/editing/workspaces/multi-root-workspaces "https://code.visualstudio.com/docs/editing/workspaces/multi-root-workspaces").

This capability is currently scoped to the editor window.

[Agent hooks](https://code.visualstudio.com/docs/agent-customization/hooks "https://code.visualstudio.com/docs/agent-customization/hooks") remain scoped to a single workspace folder. If hooks are detected in multiple folders, VS Code prompts you to select the primary folder from which to load them.

### Redesigned new-session input

Start delegated work with less setup in the redesigned new-session input. The updated experience brings the prompt, model selection, workspace selection, and other session controls together in one layout.

![Screenshot of the redesigned new-session input in the Agents window with context, permission, worktree, and branch controls.](https://code.visualstudio.com/raw/images/1_136/agents-new-session-input.webp)

### Improved workspace resolution

Agents can resolve workspaces by their project name in addition to absolute paths and workspace URIs. Session tools also preserve project URIs and all working directories for multi-root workspaces.

As a result, you can make requests such as "run this in the vscode workspace" without providing a full path. If multiple workspaces have the same name, the agent reports the possible matches instead of silently choosing one. Remote workspace URIs are supported as well.

### Navigate related chats and sessions

Keep related agent work organized and move between sessions and chats from the sessions list in the Agents window. Chats appear as children of their parent session, so you can understand which chats belong together without managing a collection of unrelated sessions.

Each chat row shows its own title, status, and pending approvals, so you can see which chat needs your input. Expand or collapse the hierarchy, and open, rename, move, or delete individual chats directly from the tree.

When an agent delegates independent work to multiple chats, each created chat gets a meaningful title and appears in this hierarchy.

The new session or chat is placed close to its source, and the receiving request includes a source link such as **Sent by another session** or **Sent from another chat**. Select the link to return to the exact session or chat that initiated it.

![Screenshot showing a delegated request with a Sent from another chat source link.](https://code.visualstudio.com/raw/images/1_136/session-chat-source.webp)

### Readable breadcrumbs for session files

Files created in the internal session state directory previously showed internal session identifiers in editor breadcrumbs. Breadcrumbs now use stable provider and session labels, making it easier to identify the file location without exposing implementation details.

![Screenshot showing readable session labels in the breadcrumbs for an agent-created file.](https://code.visualstudio.com/raw/images/1_136/session-breadcrumbs.webp)

### Chat backgrounds in the Agents window (Experimental)

**Settings**: `chat.agentSessions.preferredDarkBackgroundImage`, `chat.agentSessions.preferredLightBackgroundImage`, `chat.agentSessions.backgroundImageLayout`

Personalize the Agents window with a decorative chat background: either a theme-aware pattern of built-in VS Code icons or an image of your own.

Run **Chat: Set Background...** to choose between the **Codicons** pattern and an image from your machine. The five images you used most recently are offered under **Recently Used**, and that list is kept on this machine only.

![Screenshot showing the Codicons pattern behind the new session input in the Agents window.](https://code.visualstudio.com/raw/images/1_136/agents-chat-background-codicons.webp)

When you bring your own image, run **Chat: Change Background Layout...** to place it. Eleven layouts are available: **Repeat**, **Stretch**, **Center**, and each edge and corner. Moving through the list previews each layout in place, so you can judge the result before committing to it. **Chat: Clear Background** returns to the plain surface.

Dark and light themes keep separate backgrounds. Every dark theme shares `chat.agentSessions.preferredDarkBackgroundImage` and every light theme shares `chat.agentSessions.preferredLightBackgroundImage`, so switching between a dark and a light theme swaps the background along with it. High contrast themes suppress backgrounds entirely, and the three commands are unavailable there.

Chat content carries its own fill so that it stays readable over whatever sits behind it. Your request remains fully opaque, agent responses fade out through the padding on either side, and wide content such as Markdown tables and terminal output stays fully backed.

![Screenshot showing an agent response and a Markdown table remaining readable over the Codicons background.](https://code.visualstudio.com/raw/images/1_136/agents-chat-background-readability.webp)

Learn more about [personalizing chat](https://code.visualstudio.com/docs/chat/chat-overview#_personalize-chat "https://code.visualstudio.com/docs/chat/chat-overview#_personalize-chat").

### Agent session notifications

**Settings**:   `[chat.notifyWindowOnConfirmation](code-setting://chat.notifyWindowOnConfirmation "View or change setting")` ,   `[chat.notifyWindowOnResponseReceived](code-setting://chat.notifyWindowOnResponseReceived "View or change setting")`

VS Code can notify you when an agent session needs your input or finishes its work. This is especially useful when you delegate work across multiple sessions, workspaces, or VS Code windows.

By default, notifications only appear when the VS Code window is not focused. You can configure notifications separately for sessions that need input and sessions that have received a response. Notifications include a direct link back to the relevant session, so selecting one focuses the correct window and opens the session that needs attention.

### Agent Merge (Preview)

**Setting**:   `[chat.agentMerge.enabled](code-setting://chat.agentMerge.enabled "View or change setting")`

Agent Merge helps you take a pull request across the finish line. It asks an agent to address review feedback, fix failed checks and merge conflicts, and rerun workflows. Agent Merge repeats this process until the pull request is ready to merge.

To try Agent Merge, enable   `[chat.agentMerge.enabled](code-setting://chat.agentMerge.enabled "View or change setting")` . You can currently enable Agent Merge for a session only from the Agents window. Run **Enable Agent Merge for Active Session** or select the **Agent Merge** button in the title bar. Learn more about [using Agent Merge](https://code.visualstudio.com/docs/agents/run/agents-window#_finish-a-pull-request-with-agent-merge "https://code.visualstudio.com/docs/agents/run/agents-window#_finish-a-pull-request-with-agent-merge").

### Agent host

The agent host lets you connect to the same agent session from multiple VS Code windows. It runs agent harnesses in a dedicated process based on the [Agent Host Protocol](https://microsoft.github.io/agent-host-protocol/ "https://microsoft.github.io/agent-host-protocol/") (AHP). The agent host's Copilot agent is powered by the [Copilot SDK](https://www.npmjs.com/package/@github/copilot-sdk "https://www.npmjs.com/package/@github/copilot-sdk"), which aligns the agent's behavior and functionality with the Copilot CLI, the standalone GitHub Copilot app, and other Copilot products.

We're actively developing the agent host. The following screenshot shows the `Copilot` harness selected for an agent host in an editor window:

![Screenshot showing the harness dropdown in the editor window.](https://code.visualstudio.com/raw/images/1_136/agent-host-harness-dropdown-editor.webp)

Learn more in the [agent host documentation](https://code.visualstudio.com/docs/agents/concepts/agent-host "https://code.visualstudio.com/docs/agents/concepts/agent-host") and our new [agent host blog post](https://code.visualstudio.com/blogs/2026/08/26/agent-host-architecture "https://code.visualstudio.com/blogs/2026/08/26/agent-host-architecture"), where we share why we built the agent host, what it enables in VS Code, how the architecture and open protocol work, and workflows you can try yourself.

If you have any feedback or requests, please let us know by [filing an issue](https://github.com/microsoft/vscode/issues "https://github.com/microsoft/vscode/issues").

## Chat

### Enterprise controls for dictation data

Administrators can manage the dictation model and language-model transcript cleanup through enterprise policies.

The new controls make it possible to require on-device transcription and disable language-model cleanup, so dictation remains available while preventing dictation data from being sent to cloud transcription or a Copilot model. Learn more about [enterprise controls for dictation data](https://code.visualstudio.com/docs/enterprise/ai-settings#control-dictation-data "https://code.visualstudio.com/docs/enterprise/ai-settings#control-dictation-data").

## Accessibility

### Screen Reader Optimized badge in the Agents window

The **Screen Reader Optimized** badge in the Agents window title bar makes the active accessibility mode easier to identify. The badge appears when Screen Reader Optimized mode is enabled. Select the badge to disable this mode.

![Screenshot of the Screen Reader Optimized badge in the Agents window title bar.](https://code.visualstudio.com/raw/images/1_136/agents-screen-reader-optimized-badge.webp)

## Editor experience

### Layout density for the editor window (Experimental)

**Settings**:   `[workbench.experimental.modernUI](code-setting://workbench.experimental.modernUI "View or change setting")` ,   `[window.density.layout](code-setting://window.density.layout "View or change setting")`

Fit more content in the editor window with the **Compact** layout density. When   `[workbench.experimental.modernUI](code-setting://workbench.experimental.modernUI "View or change setting")` is enabled, you can choose between two layout densities:

- **Default** layout density is the same as the current editor window layout.
- **Compact** layout density removes the spacing between panels and reduces inner panel spacing.

This setting is available in the **Layout Density** section of the Settings menu and can also be set using   `[window.density.layout](code-setting://window.density.layout "View or change setting")` .

## Code editing

### Word wrapping improvements

Injected text no longer pushes wrapped lines outside the editor viewport. Word wrapping takes the visual width of color decorators, inlay hint spacing, inline progress indicators, and breakpoint placeholders into account. Please have a look below for the before and after screenshots. On the picture above you can see that rgba is slightly cropped. While on the second picture it isn't.

![Screenshot showing a wrapped CSS line cropped at the edge of the editor viewport.](https://code.visualstudio.com/raw/images/1_136/word-wrapping-before.jpg)

![Screenshot showing the wrapped CSS line fitting within the editor viewport.](https://code.visualstudio.com/raw/images/1_136/word-wrapping-after.jpg)

## Integrated browser

### Spell check suggestions

Right-click a misspelled word in an editable field to select a suggested correction. In sessions that use persistent data storage, you can also select **Add to Dictionary**.

![Screenshot showing spelling suggestions and Add to Dictionary in the integrated browser context menu.](https://code.visualstudio.com/raw/images/1_136/spell-check.webp)

## Terminal

### Reduced delay when running commands

Terminal commands executed by extensions no longer incur an unnecessary delay when shell integration is ready under certain timing conditions. Users of the JavaScript debugger who hit this case will no longer experience a five-second delay when starting their programs.

## Deprecated features and settings

None

## Thank you

Contributions to `vscode`:

- [@abmahdy (Ahmed Mahdy)](https://github.com/abmahdy "https://github.com/abmahdy"): Bound concurrency of prompt file discovery reads [PR #331855](https://github.com/microsoft/vscode/pull/331855 "https://github.com/microsoft/vscode/pull/331855")
- [@DanTup (Danny Tuppeny)](https://github.com/DanTup "https://github.com/DanTup"): Note that InlayHints with the same position are shown in-order [PR #175525](https://github.com/microsoft/vscode/pull/175525 "https://github.com/microsoft/vscode/pull/175525")
- [@davidbitton (David B. Bitton)](https://github.com/davidbitton "https://github.com/davidbitton"): Add spelling suggestions to the Integrated Browser context menu [PR #333043](https://github.com/microsoft/vscode/pull/333043 "https://github.com/microsoft/vscode/pull/333043")
- [@JeffreyCA](https://github.com/JeffreyCA "https://github.com/JeffreyCA"): Update Fig spec for Azure Developer CLI (azd) [PR #331727](https://github.com/microsoft/vscode/pull/331727 "https://github.com/microsoft/vscode/pull/331727")
- [@juliagongms (Julia Gong)](https://github.com/juliagongms "https://github.com/juliagongms"): nes: apply supportsUnifiedCompletions on the default provider path [PR #332802](https://github.com/microsoft/vscode/pull/332802 "https://github.com/microsoft/vscode/pull/332802")
- [@koubaki](https://github.com/koubaki "https://github.com/koubaki"): Update error message in inlineChatIntent.ts [PR #329157](https://github.com/microsoft/vscode/pull/329157 "https://github.com/microsoft/vscode/pull/329157")
- [@ktsoator (ktsoator)](https://github.com/ktsoator "https://github.com/ktsoator"): Hover: restore scrolling for long content [PR #331439](https://github.com/microsoft/vscode/pull/331439 "https://github.com/microsoft/vscode/pull/331439")
- [@na2co3-ftw (na2co3)](https://github.com/na2co3-ftw "https://github.com/na2co3-ftw"): Modern UI: Fix CSS specificity for tab action fading [PR #332103](https://github.com/microsoft/vscode/pull/332103 "https://github.com/microsoft/vscode/pull/332103")
- [@preitinger (Peter Reitinger)](https://github.com/preitinger "https://github.com/preitinger"): Update snippet.md [PR #231790](https://github.com/microsoft/vscode/pull/231790 "https://github.com/microsoft/vscode/pull/231790")
- [@remcohaszing (Remco Haszing)](https://github.com/remcohaszing "https://github.com/remcohaszing")
    - Normalize end of line cursor move operation [PR #296712](https://github.com/microsoft/vscode/pull/296712 "https://github.com/microsoft/vscode/pull/296712")
    - Fix out of bounds text selection with line wrapping [PR #262910](https://github.com/microsoft/vscode/pull/262910 "https://github.com/microsoft/vscode/pull/262910")
    - Round custom line heights [PR #298421](https://github.com/microsoft/vscode/pull/298421 "https://github.com/microsoft/vscode/pull/298421")
    - Expose the score function in Monaco editor [PR #322959](https://github.com/microsoft/vscode/pull/322959 "https://github.com/microsoft/vscode/pull/322959")
- [@SimonSiefke (Simon Siefke)](https://github.com/SimonSiefke "https://github.com/SimonSiefke")
    - fix: memory leak in explorer viewer [PR #332332](https://github.com/microsoft/vscode/pull/332332 "https://github.com/microsoft/vscode/pull/332332")
    - fix: memory leak in LSP terminal completions [PR #332173](https://github.com/microsoft/vscode/pull/332173 "https://github.com/microsoft/vscode/pull/332173")
- [@TheNotary](https://github.com/TheNotary "https://github.com/TheNotary"): Update error message for unsupported skill attributes [PR #328318](https://github.com/microsoft/vscode/pull/328318 "https://github.com/microsoft/vscode/pull/328318")
- [@tisilent (xiejialong)](https://github.com/tisilent "https://github.com/tisilent"): update label and description. [PR #219949](https://github.com/microsoft/vscode/pull/219949 "https://github.com/microsoft/vscode/pull/219949")
- [@unsupportedpastels (Mark S.)](https://github.com/unsupportedpastels "https://github.com/unsupportedpastels"): Support reasoning effort in custom agent files [PR #329263](https://github.com/microsoft/vscode/pull/329263 "https://github.com/microsoft/vscode/pull/329263")
- [@weidehai (io)](https://github.com/weidehai "https://github.com/weidehai"): error correction instructions [PR #249715](https://github.com/microsoft/vscode/pull/249715 "https://github.com/microsoft/vscode/pull/249715")

Contributions to `vscode-emmet-helper`:

- [@danfiedler-msft (Dan Fiedler)](https://github.com/danfiedler-msft "https://github.com/danfiedler-msft"): Pin GitHub Actions to full-length commit SHAs [PR #108](https://github.com/microsoft/vscode-emmet-helper/pull/108 "https://github.com/microsoft/vscode-emmet-helper/pull/108")

Contributions to `vscode-livepreview`:

- [@danfiedler-msft (Dan Fiedler)](https://github.com/danfiedler-msft "https://github.com/danfiedler-msft"): Pin GitHub Actions to full-length commit SHAs [PR #854](https://github.com/microsoft/vscode-livepreview/pull/854 "https://github.com/microsoft/vscode-livepreview/pull/854")

Contributions to `docfind`:

- [@danfiedler-msft (Dan Fiedler)](https://github.com/danfiedler-msft "https://github.com/danfiedler-msft"): Pin GitHub Actions to full-length commit SHAs [PR #62](https://github.com/microsoft/docfind/pull/62 "https://github.com/microsoft/docfind/pull/62")

Contributions to `node-pty`:

- [@danfiedler-msft (Dan Fiedler)](https://github.com/danfiedler-msft "https://github.com/danfiedler-msft"): Pin GitHub Actions to full-length commit SHAs [PR #958](https://github.com/microsoft/node-pty/pull/958 "https://github.com/microsoft/node-pty/pull/958")

### Issue tracking

Contributions to our issue tracking:

- [@gjsjohnmurray (John Murray)](https://github.com/gjsjohnmurray "https://github.com/gjsjohnmurray")
- [@saroasid-web (Saswwo)](https://github.com/saroasid-web "https://github.com/saroasid-web")
- [@zotabee (zotabee)](https://github.com/zotabee "https://github.com/zotabee")
- [@lppedd (Edoardo Luppi)](https://github.com/lppedd "https://github.com/lppedd")
- [@sandstrom (sandstrom)](https://github.com/sandstrom "https://github.com/sandstrom")

---

We really appreciate people trying our new features as soon as they are ready, so check back here often and learn what's new.

> If you'd like to read release notes for previous VS Code versions, go to [Updates](https://code.visualstudio.com/updates "https://code.visualstudio.com/updates") on [code.visualstudio.com](https://code.visualstudio.com/ "https://code.visualstudio.com").