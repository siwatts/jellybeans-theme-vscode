# Jellybeans Theme

## About

This theme is based on the popular vim theme [jellybeans.vim by
nanotech](https://github.com/nanotech/jellybeans.vim), ported to the syntax
highlighting groups of the default Dark+ theme.

We use the comprehensive syntax highlighting groups of the default Dark+ theme
for VS Code, but with the colour palette from jellybeans.vim. Where possible,
jellybeans.vim syntax highlighting is preferred. For example, the Dark+ teal
green used for class names has been replaced everywhere by the jellybeans.vim
`:hi Type` orange/yellow. The Dark+ red string highlight has been replaced by
jellybeans.vim `:hi String` green, always choosing the jellybeans.vim syntax
highlight colour which closest reflects the meaning of the Dark+ element.

Although starting as a 1:1 colour swap into Dark+ theme, small modifications may
be made to bring things more in line with jellybeans.vim appearance. Due to the
different way that VS Code and vim highlight code it is not possible to fully
replicate jellybeans.vim across all languages, and parity with the Dark+ theme
is preferred over trying to recreate every element of jellybeans.vim.

## Screenshots

![Jellybeans.vim C code example](img/Screenshot_from_2022-08-31_18-01-22.png?raw=true "C code example")
![Jellybeans.vim package.json example](img/Screenshot_from_2022-08-31_17-52-58.png?raw=true "UI example - package.json")
![Jellybeans.vim C code example 2](img/Screenshot_from_2022-08-31_18-01-34.png?raw=true "C code example, 2")

Screenshots from v0.0.2 which would become v1.0.0

## Customisation

| Add to your `settings.json` to override colour options |
| --- |

Remove some variable / identifier highlighting:
- VS Code by default highlights all identified variables, which when
  Intellisense is working is pretty much everything on screen
- Can remove this and get foreground text colour back, leaving only function
  parameters and similar to be highlighted
- This will give more of a legacy vim style look

```json
"editor.tokenColorCustomizations": {
    "[Jellybeans.vim]": {
        // Disable some variable highlighting
        "textMateRules": [
            { "scope": "variable.parameter", "settings": { "foreground": "#c6b6ee", "fontStyle": "", }, },
            { "scope": "variable.other", "settings": { "foreground": "#e8e8d3", "fontStyle": "", }, },
        ],
    },
},
```

Brighter bracket pair matching:
- Bracket pair matching is based first on jellybeans.vim `:hi Delimiter` colour,
  then rotating around similar colours.
- To use brighter colours from theme and make brackets more legible, use
  something like this

```json
"workbench.colorCustomizations": {
    "[Jellybeans.vim]": {
        "editorBracketHighlight.foreground1": "#8fbfdc",
        "editorBracketHighlight.foreground2": "#ffb964",
        "editorBracketHighlight.foreground3": "#8197bf",
        "editorBracketHighlight.foreground4": "#cf6a4c",
        "editorBracketHighlight.foreground5": "#99ad6a",
        "editorBracketHighlight.foreground6": "#fad07a",
    },
},
```

## Version History

| Version | Notes |
| ------- | ----- |
| v0.9.0  | First draft, 1:1 colour swap from jellybeans.vim into Dark+, plus UI elements |
| v1.0.0  | Minor revisions. Bracket pair matching, enums more consistent with vim theme, dark green incorporated etc. |

## Future

- "Legacy theme" option, targetting more vim compatibility and less Dark+ theme
  parity.
    - Less blanket variable/identifier highlighting (see Customisation above)
    - More fine tuned vim based highlighting groups
        - Preproc commands -> light blue
        - Preproc defines -> constant red where used (like enums)
    - `:hi StorageClass` brown incorporation
    - `:hi Special` dark green for string escapes
    - Python `this`, `self` keywords are `:hi Special` dark green in nvim
      TreeSitter highlighting?

