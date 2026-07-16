#vscode
## Folding

In VS Code you can fold regions of source code using the folding icons on the gutter between line numbers and line start. Move the mouse over the gutter and click to fold and unfold regions. Use `Shift + Click` on the folding icon to fold or unfold the region and all regions inside.

![[folding-basic-editing.png]]

You can also use the following actions:

- Fold (`Ctrl+Shift+[`) folds the innermost uncollapsed region at the cursor.
- Unfold (`Ctrl+Shift+]`) unfolds the collapsed region at the cursor.
- Toggle Fold (`Ctrl+K Ctrl+L`) folds or unfolds the region at the cursor.
- Fold Recursively (`Ctrl+K Ctrl+[`) folds the innermost uncollapsed region at the cursor and all regions inside that region.
- Unfold Recursively (`Ctrl+K Ctrl+]`) unfolds the region at the cursor and all regions inside that region.
- Fold All (`Ctrl+K Ctrl+0`) folds all regions in the editor.
- Unfold All (`Ctrl+K Ctrl+J`) unfolds all regions in the editor.
- Fold Level X (`Ctrl+K Ctrl+2` for level 2) folds all regions of level X, except the region at the current cursor position.
- Fold All Block Comments (`Ctrl+K Ctrl+/`) folds all regions that start with a block comment token.

Regions can also be defined by markers defined by each language. The following languages currently have markers defined:

![[start-end-regions-languages.png]]