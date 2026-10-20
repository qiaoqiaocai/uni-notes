# uni-notes
University Obsidian notes published in a Jekyll Page.

Using Enveloppe Obsidian plugin to publish `share: true` .md notes in the `page/` folder.

Uses Enveloppe's text replacer to change every single $ to $$.
- regex of the text to replace: `/(?<!\$)\$([^$]+?)\$(?!\$)/`
- replacement: `$$$$$1$$$$`
