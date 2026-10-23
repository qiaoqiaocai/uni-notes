# uni-notes
University Obsidian notes published in a Jekyll Page.

Using Enveloppe Obsidian plugin to publish `share: true` .md notes in the `page/` folder.

## Enveloppe's text replacer configurations
to change every single $ to $$.
- regex of the text to capture: `/(?<!\$)\$([^$]+?)\$(?!\$)/`
- replacement: `$$$$$1$$$$`

to encapsule codeblocks in \{::nomarkdown\} \{:/nomarkdown\}
- regex of the text to capture: `/<([a-zA-Z][\w-]*)\b[^>]*>[\s\S]*?</\1\s*>/`
- replacement: `{::nomarkdown} $& {:/nomarkdown}`

## Resources used
Table of Contents generation: (jekyll-toc)[https://github.com/allejo/jekyll-toc]

Jekyll theme: (minimal)[https://github.com/pages-themes/minimal]

Markdown codeblock style: (my-jekyll-syntax-highlighter-theme)[https://github.com/low-perry/my-jekyll-syntax-highlighter-theme]
