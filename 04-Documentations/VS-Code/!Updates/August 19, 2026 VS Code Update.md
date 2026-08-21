#vscode-update 


# Visual Studio Code 1.134

Show release notes after an update

Follow us on [LinkedIn](https://www.linkedin.com/showcase/vs-code "https://www.linkedin.com/showcase/vs-code"), [X](https://go.microsoft.com/fwlink/?LinkID=533687 "https://go.microsoft.com/fwlink/?LinkID=533687"), [Bluesky](https://bsky.app/profile/vscode.dev "https://bsky.app/profile/vscode.dev") | [View online](https://code.visualstudio.com/updates "https://code.visualstudio.com/updates")

---

_Release date: August 19, 2026_

---

Welcome to the 1.134 release of Visual Studio Code. This release helps you work across windows, organize related chats side by side, and navigate long conversations faster.

- [Side-by-side chats](https://code.visualstudio.com/raw/#grid-layout-for-chats-in-a-session "#grid-layout-for-chats-in-a-session"): Arrange related chats and subagent chats in groups for easier comparison.
    
- [Prompt timeline](https://code.visualstudio.com/raw/#prompt-timeline "#prompt-timeline"): Quickly navigate across prompts and review their file changes.
    
- [Find in chat](https://code.visualstudio.com/raw/#find-in-chat "#find-in-chat"): Search for text in the complete conversation with ease.
    
- [Preview HTML files](https://code.visualstudio.com/raw/#open-html-files-in-the-integrated-browser-by-default "#open-html-files-in-the-integrated-browser-by-default"): Preview local HTML files directly in VS Code by making the integrated browser their default editor.
    

Happy Coding!

---

VS Code is rolling out gradually to all users. Use **Check for Updates** in VS Code to get the latest version immediately.

To try new features as soon as possible, [**download the nightly Insiders build**](https://code.visualstudio.com/insiders "https://code.visualstudio.com/insiders"), which includes the latest updates as soon as they are available.

---

In this update

- [[August 19, 2026 VS Code Update#Agents|Agents]]
- [[August 19, 2026 VS Code Update#Chat|Chat]]
- [[August 19, 2026 VS Code Update#Editor Experience|Editor Experience]]
- [[August 19, 2026 VS Code Update#Thank you|Thank you]]

## Agents

### Agent host

The agent host lets you connect to the same agent session from multiple VS Code windows. It runs agent harnesses in a dedicated process based on the [Agent Host Protocol](https://microsoft.github.io/agent-host-protocol/ "https://microsoft.github.io/agent-host-protocol/") (AHP). The agent host's Copilot agent is powered by the [Copilot SDK](https://www.npmjs.com/package/@github/copilot-sdk "https://www.npmjs.com/package/@github/copilot-sdk"), which aligns the agent's behavior and functionality with the Copilot CLI, the standalone GitHub Copilot app, and other Copilot products.

We're actively developing the agent host. The following screenshot shows the `Copilot` harness selected for an agent host in an editor window:

![Screenshot showing the harness dropdown in the editor window.](https://code.visualstudio.com/raw/images/1_134/agent-host-harness-dropdown-editor.webp)

You can learn more in our [VS Code Agent Host documentation](https://code.visualstudio.com/docs/agents/concepts/agent-host "https://code.visualstudio.com/docs/agents/concepts/agent-host"). If you have any feedback or requests, please let us know by [filing an issue](https://github.com/microsoft/vscode/issues "https://github.com/microsoft/vscode/issues").

### Grid layout for chats in a session

Keep related conversations visible by arranging chats in horizontal or vertical groups. Drag chats or subagent chats into a group to compare results or monitor work side by side. VS Code restores the chat-group layout and focus when you return to the session or reload the window.

Create a side chat to open a new conversation beside the current chat.

Drag and drop a subagent chat into a group to view it side by side with the current chat.

You can also Alt+select a chat in the **Chats** picker to open it to the side.

### Improvements to the side pane layout

**Settings**: `sessions.layout.singlePaneDetailPanel` and   `[workbench.editor.showTabs](code-setting://workbench.editor.showTabs "View or change setting")`

The single-pane layout keeps session details and editors in a shared tab bar next to chat. This release makes the layout easier to control:

- The layout follows the   `[workbench.editor.showTabs](code-setting://workbench.editor.showTabs "View or change setting")` setting. Multiple tabs remain visible, while the `single` and `none` values use a compact single-title header.
    
    ![Screenshot showing the compact single-title header in the Agents window.](https://code.visualstudio.com/raw/images/1_134/agents-window-single-tab.webp)
    
- Text file editors use the same header structure as the Changes editor, with file breadcrumbs in the header.
    
- The side pane keeps its size and visibility when you switch sessions, avoiding unexpected layout shifts.
    

Enable `sessions.layout.singlePaneDetailPanel` and reload the window to use this layout.

### Prompt timeline

**Setting**:   `[sessions.chatTimeline.display](code-setting://sessions.chatTimeline.display "View or change setting")`

Long agent sessions can make it difficult to find earlier prompts and identify which ones changed files.

The Agents window includes a timeline in the transcript gutter. Each dot represents one of your prompts, and the highlighted dot marks your current position. Hover over the timeline to view your prompts, then select one to jump to it. For prompts that changed files, the list shows the number of lines added and removed and lets you open the changes directly for review.

Use the   `[sessions.chatTimeline.display](code-setting://sessions.chatTimeline.display "View or change setting")` setting to show the timeline beside the scrollbar (`ruler`) or hide it (`off`).

## Chat

### Find in chat

Finding information from earlier in a long conversation previously required scrolling through the transcript. Use `Ctrl+F` to search conversations in the Chat view, chat editors, and the Agents window.

Search includes the entire conversation, even content that is not currently rendered on screen. As you move between matches, VS Code scrolls each match into view and expands a collapsed work summary if it contains the match. You can also match case, match whole words, or use regular expressions.

## Editor Experience

### Close other editors from a tab

Keep one editor open without using the tab context menu. Hold `Alt` to change the close action on each editor tab to **Close Other Editors**, then select the action on the tab you want to keep.

### Open HTML files in the integrated browser by default

**Setting**:   `[workbench.editorAssociations](code-setting://workbench.editorAssociations "View or change setting")`

If you often preview local HTML files instead of editing them, set the integrated browser as their default editor. Configure this behavior with the   `[workbench.editorAssociations](code-setting://workbench.editorAssociations "View or change setting")` setting or from the editor header.

The integrated browser provides the same features as a standalone browser tab while remaining associated with the HTML file. To preserve this association, links and other navigation open in new tabs.

## Thank you

Contributions to `vscode`:

- [@a1exmozz](https://github.com/a1exmozz "https://github.com/a1exmozz"): agentHost: Emit user message telemetry to CTS [PR #329961](https://github.com/microsoft/vscode/pull/329961 "https://github.com/microsoft/vscode/pull/329961")
- [@abmahdy (Ahmed Mahdy)](https://github.com/abmahdy "https://github.com/abmahdy"): Preserve instructions for terminal completion notifications [PR #330570](https://github.com/microsoft/vscode/pull/330570 "https://github.com/microsoft/vscode/pull/330570")
- [@benelog (Sanghyuk Jung)](https://github.com/benelog "https://github.com/benelog"): Fix duplicated word in Copilot prompt text [PR #328961](https://github.com/microsoft/vscode/pull/328961 "https://github.com/microsoft/vscode/pull/328961")
- [@cipheraxat (Akshat Anand)](https://github.com/cipheraxat "https://github.com/cipheraxat"): Modern UI tabs: reserve close-button column so it doesn't overlay filename (fix #329605) [PR #330754](https://github.com/microsoft/vscode/pull/330754 "https://github.com/microsoft/vscode/pull/330754")
- [@jadefr (Jade Ferreira Vieira)](https://github.com/jadefr "https://github.com/jadefr"): Feature/alt click close other tabs [PR #328975](https://github.com/microsoft/vscode/pull/328975 "https://github.com/microsoft/vscode/pull/328975")
- [@martincheck (Martin Check)](https://github.com/martincheck "https://github.com/martincheck"): chat: avoid splitting surrogate pairs in read_file [PR #331005](https://github.com/microsoft/vscode/pull/331005 "https://github.com/microsoft/vscode/pull/331005")
- [@marvinroger (Marvin ROGER)](https://github.com/marvinroger "https://github.com/marvinroger"): Fix crash due to undefined `document.queryCommandSupported` [PR #330298](https://github.com/microsoft/vscode/pull/330298 "https://github.com/microsoft/vscode/pull/330298")
- [@mirimadahmed (Mir)](https://github.com/mirimadahmed "https://github.com/mirimadahmed"): voice: honor the new_session flag on send_to_chat [PR #330859](https://github.com/microsoft/vscode/pull/330859 "https://github.com/microsoft/vscode/pull/330859")
- [@Shaurav-Vora (Shaurav Vora)](https://github.com/Shaurav-Vora "https://github.com/Shaurav-Vora"): Co-authored: Implement Ctrl+F find widget support for chat panes and editors [PR #330340](https://github.com/microsoft/vscode/pull/330340 "https://github.com/microsoft/vscode/pull/330340")
- [@SimonSiefke (Simon Siefke)](https://github.com/SimonSiefke "https://github.com/SimonSiefke")
    - fix: memory leak in extensions view [PR #330210](https://github.com/microsoft/vscode/pull/330210 "https://github.com/microsoft/vscode/pull/330210")
    - fix: memory leak in source control view [PR #330241](https://github.com/microsoft/vscode/pull/330241 "https://github.com/microsoft/vscode/pull/330241")
    - fix: memory leak in code actions [PR #330142](https://github.com/microsoft/vscode/pull/330142 "https://github.com/microsoft/vscode/pull/330142")
    - fix: memory leak in search view [PR #330240](https://github.com/microsoft/vscode/pull/330240 "https://github.com/microsoft/vscode/pull/330240")
    - fix: memory leaks in chat widgets [PR #326876](https://github.com/microsoft/vscode/pull/326876 "https://github.com/microsoft/vscode/pull/326876")
    - fix: memory leak in references view [PR #330191](https://github.com/microsoft/vscode/pull/330191 "https://github.com/microsoft/vscode/pull/330191")
    - fix: memory leak in search result folder matches [PR #331012](https://github.com/microsoft/vscode/pull/331012 "https://github.com/microsoft/vscode/pull/331012")
- [@yzxcj797](https://github.com/yzxcj797 "https://github.com/yzxcj797"): docs: fix dead nes-video.gif link in copilot extension README [PR #330992](https://github.com/microsoft/vscode/pull/330992 "https://github.com/microsoft/vscode/pull/330992")

### Issue tracking

Contributions to our issue tracking:

- [@gjsjohnmurray (John Murray)](https://github.com/gjsjohnmurray "https://github.com/gjsjohnmurray")
- [@RedCMD (RedCMD)](https://github.com/RedCMD "https://github.com/RedCMD")
- [@IllusionMH (Andrii Dieiev)](https://github.com/IllusionMH "https://github.com/IllusionMH")
- [@albertosantini (Alberto Santini)](https://github.com/albertosantini "https://github.com/albertosantini")

---

We appreciate people trying our new features as soon as they are ready. Check back often to learn what's new.

> If you'd like to read release notes for previous VS Code versions, go to [Updates](https://code.visualstudio.com/updates "https://code.visualstudio.com/updates") on [code.visualstudio.com](https://code.visualstudio.com/ "https://code.visualstudio.com").