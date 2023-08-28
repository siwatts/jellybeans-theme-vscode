# Jellybeans Theme

## About

Based on the popular vim theme [jellybeans.vim by
nanotech](https://github.com/nanotech/jellybeans.vim), with the syntax
highlighting of vscode's Dark+.

Package supplies two themes:

- Jellybeans+
    - Powerful *Dark+* syntax highlighting groups, now with Jellybeans colours!
- Jellybeans.vim
    - Variant for that classic *vim* look
    - Brought closer to the original *jellybeans.vim* as rendered by *neovim*
      with *TreeSitter highlight* plugin where possible, or vanilla *vim*
      implementation

Theme includes UI & menus, integrated terminal, debugger syntax, and more!

## Screenshots

![Jellybeans.vim C code example](img/Screenshot_from_2023-08-28_21-47-31.png?raw=true "C code example")
![Jellybeans.vim C code example 2](img/Screenshot_from_2023-08-28_21-47-59.png?raw=true "C code example, 2")
![Jellybeans.vim C code example 3](img/Screenshot_from_2023-08-28_21-48-45.png?raw=true "C code example, 3")
![Jellybeans.vim package.json example](img/Screenshot_from_2023-08-28_22-06-03.png?raw=true "UI example - package.json")

Screenshots from v1.1.4

Font: IBM Plex Mono Regular

## Description

Rather than attempting to recreate jellybeans vim theme in VS Code from scratch,
the comprehensive syntax highlighting groups of the default Dark+ theme for VS
Code are used and substituted with jellybeans.vim colours. This should preserve
the powerful syntax highlighting abilities of VS Code, and result in a theme
which looks good over multiple languages while having the look and feel of vim
jellybeans.

Although starting as a 1:1 colour swap into Dark+ theme, modifications are
made to bring things more in line with jellybeans.vim appearance.

There are currently two variants, one leaning more towards 1:1 Dark+ syntax
highlighting groups, and one which seeks more to emulate jellybeans.vim as seen
in vim (and neovim). It is not possible to fully replicate vim syntax
highlighting groups in VS Code, but where possible inspiration is taken from
`jellybeans.vim` as rendered by `neovim` with the plugin `TreeSitter highlight`
enabled.

## Customisation

On Linux to enable jellybeans theme titlebars and menu UI items you can add the
following to your vscode `settings.json` file:

```json
"window.titleBarStyle": "custom",
"window.dialogStyle": "custom",
```

| Add to your `settings.json` to override individual colour options by theme |
| --- |

Remove some variable / identifier highlighting:
- VS Code by default highlights all identified variables, which when
  Intellisense is working is pretty much everything on screen
- Can remove this and get foreground text colour back, leaving only function
  parameters and similar to be highlighted
- This will give more of a legacy vim style look
- *Jellybeans.vim* variant already includes this change

```json
"editor.tokenColorCustomizations": {
    "[Jellybeans+][Jellybeans.vim]": {
        // Disable some variable highlighting
        "textMateRules": [
            { "scope": "variable.parameter", "settings": { "foreground": "#c6b6ee", "fontStyle": "", }, },
            { "scope": "variable.other", "settings": { "foreground": "#e8e8d3", "fontStyle": "", }, },
        ],
    },
},
```

Brighter bracket pair matching:
- Bracket pair matching is based first on jellybeans vim `:hi Delimiter` colour,
  then rotating around similar colours.
- To use brighter colours taken from the theme itself and make brackets more
  legible, use something like this

```json
"workbench.colorCustomizations": {
    "[Jellybeans+][Jellybeans.vim]": {
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
| v1.1.0  | Split into *Jellybeans+* and *Jellybeans.vim* variants, plus debugging colours |
| v1.1.1  | Minor fixes and enhancements, *Jellybeans.vim* brought closer to neovim |
| v1.1.2  | Minor enhancements, *Jellybeans.vim* brought closer to neovim. Lower min. vscode vers. requirement |
| v1.1.3  | Add or modify general UI colours and search highlighting |
| v1.1.4  | Remove semantic `macro` definition for *Jellybeans.vim* |

## Future

Possible future developments

- More fine tuned vim based highlighting groups
    - C/C++ preproc defines -> constant red where they are used (like enums)
      - Semantic group `macro` covers this but also where they are defined
    - Python "None" and other language constants are `:hi Special` dark green in
      nvim. They get clobbered by language constants (True/False) mapping
      currently
- Light variant
  - Based on light colours from hybrid.vim or other bespoke colours
- Other contrast variants
  - Refactor code to allow for other colour palettes
  - Pale contrast based on hybrid.vim colours
  - Twilight colours
  - Wombat colours
  - Jellybeans-Bright colours
- Break out 3rd variant
  - Use other colours, from jellybeans.vim or otherwise
    - Pinks and blues for ruby from theme are currently unused
  - Namespaces colour change as JB+ or preproc blue
  - Keep variable highlighting
  - String escapes
  - Function decorators (python?) to pink
  - True/False & other constants
  - Semantic builtinConstant to constant red
  - Enum constants to rubyRegexp pink? StorageClass brown?
  - Self param (python) to PreProc blue, or rubyPredefinedIdentifier pale pink?
- Check if we can support older versions of VS Code
- Other language keywords to `:hi Special` green to match
  python `self`, like `this` etc.
- Something else with `storage.modifier`, because it is not actually
  `:hi StorageClass` brown in neovim with TreeSitter highlight enabled
