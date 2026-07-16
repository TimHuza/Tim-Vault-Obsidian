#vscode 
## Basic layout

VS Code comes with a simple and intuitive layout that maximizes the space provided for the editor, while leaving ample room to browse and access the full context of your folder or project. The user interface is divided into six main areas:

- **Editor** - The main area to edit your files. You can open as many editors as you like side by side vertically and horizontally.
- **Primary Side Bar** - Contains different views like the Explorer to assist you while working on your project.
- **Secondary Side Bar** - Opposite the Primary Side Bar. By default, contains the Chat view. Drag and drop views from the Primary Side Bar to the Secondary Side Bar to move them.
- **Status Bar** - Information about the opened project and the files you edit.
- **Activity Bar** - Located on the far left-hand side. Lets you switch between views and gives you additional context-specific indicators, like the number of outgoing changes when Git is enabled. You can change the position of the Activity Bar by right-clicking it to open a context menu.
- **Panel** - An additional space for views below the editor region. By default, it contains output, debug information, errors and warnings, and an integrated terminal. The Panel can also be moved to the left or right for more vertical space.

![[main-areas-ui.png|678]]

>💡 Tip
	You can move the Primary Side Bar to the right hand side by right-clicking the Activity Bar and selecting **Move Primary Side Bar Right** or toggle its visibility (`Ctrl+B`).
## Side by side editing

You can open as many editors as you like side by side vertically and horizontally. If you already have an editor open, there are multiple ways of opening another editor to the side:

- `Alt` and select a file in the Explorer view.
- `Ctrl+\` to split the active editor into two.
- **Open to the Side** (`Ctrl+Enter`) from the Explorer context menu on a file.
- Select the **Split Editor** button in the upper right of an editor.
- Drag and drop a file to any side of the editor region. Hold `Ctrl` (`Option` on macOS) while dragging to copy the tab instead of moving it.
- Press `Ctrl+Enter` in the **Quick Open** (`Ctrl+P`) file list.

When you have more than one editor open, you can switch between them quickly by holding the `Ctrl` key (`Cmd` on macOS) and pressing `1`, `2`, or `3`.

>💡 Tip
	You can resize editors and reorder them. Drag and drop the editor title area to reposition or resize the editor.

### Editor groups

When you split an editor (using the **Split Editor** or **Open to the Side** commands), a new editor region (edit group) is created which can hold a group of items. You can open as many editor groups as you like side by side vertically and horizontally.

You can see these clearly in the **Open Editors** section at the top of the Explorer view (toggle **...** > **Open Editors** in the Explorer view).

![[editor-groups-ui.png]]

> ℹ Note
	VS Code uses editor groups whether or not you have enabled tabs. Without tabs, editor groups are a stack of your open items with the most recently selected item visible in the editor pane.

## Minimap

A Minimap (code outline) gives you a high-level overview of your source code, which is useful for quick navigation and code understanding. A file's minimap is shown on the right side of the editor. You can select or drag the shaded area to quickly jump to different sections in your file.

If you have [[Basic Editing#Folding|folding markers]] in the editor, such as `//#region` comments, then the minimap shows the folding marker names. Folding markers are language-specific, so check which markers apply to your language.

![[minimap-ui.png]]

> 💡 Tip
	You can move the minimap to the left hand side or disable it completely by respectively setting `"editor.minimap.side": "left"` or `"editor.minimap.enabled": false` in the user or workspace [[Settings|settings]].

## Sticky Scroll

Sticky Scroll shows the starting lines of currently visible nested scopes at the top of the editor. It facilitates navigation by indicating where you are in a file and lets you quickly jump back to the top of the current scope.
![[sticky-scroll-ui.png]]

> 💡 Tip
	You can enable/disable Sticky Scroll with the `editor.stickyScroll.enabled` setting.

## Breadcrumbs

The editor has a navigation bar at the top, also called breadcrumbs. Breadcrumbs always show the file path and, if the current file type has language support for symbols, the symbol path up to the cursor position. The breadcrumbs enable you to quickly navigate between folders, files, and symbols.

![Breadcrumbs](https://code.visualstudio.com/assets/docs/editing/userinterface/breadcrumbs.png)

You can disable breadcrumbs with the **View** > **Appearance** > **Toggle Breadcrumbs** menu item or the **View: Toggle Breadcrumbs** command. For more information about the breadcrumbs feature, such as how to customize their appearance, see the Breadcrumbs section of the [[Code Navigation]] article.

## Explorer view

The Explorer view is used to browse, open, and manage the files and folders in your project. VS Code is file and folder based and you can get started immediately by opening a file or folder in VS Code.

After you open a folder in VS Code, the contents of the folder are shown in the Explorer view. You can do many things from here:

- Create, delete, and rename files and folders.
- Move files and folders with drag and drop.
- Use the context menu to explore all options.

>💡 Tip
	Type `Ctrl+P` (**Quick Open**) to quickly search and open a file by its name.

### Advanced tree navigation

You can filter the files and folders in the Explorer view. With the focus on the Explorer view, press `Ctrl+Alt+F` to open the Find control and type part of the file or folder name you want to match. This navigation feature is available for all tree views in VS Code.

Pressing the **Filter** button toggles between the two modes: highlighting and filtering. Pressing `Down` lets you focus on the first matched element and navigate to subsequent matching elements. In highlighting mode, a badge is shown on folders to indicate that they contain matched files.

Pressing the **Fuzzy Match** button toggles between exact and fuzzy matching, where you can type a sequence of characters to match any part of the file or folder name.

![[fuzzy-match-ui.png]]

