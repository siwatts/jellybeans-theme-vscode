# Change Log

All notable changes to the "jellybeans-theme" extension will be documented in this file.

Check [Keep a Changelog](http://keepachangelog.com/) for recommendations on how to structure this file.

## [Unreleased]

- Initial development from VS Code Dark+ theme definition files, and jellybeans.vim colours

## [0.9.0] - 2022-08-31
### Added
- New theme definitions from first development version v0.0.1
    - Mapping from jellybeans.vim colours into Dark+ theme
    - UI elements using jellybeans.vim colours and inspired colours
- First documentation, README, Images etc.

## [1.0.0] - 2022-09-01
### Added
- Theme icon png
- Changelog
### Changed
- Bracket pair matching to more subtle jellybeans.vim `:hi Delimiter` based colours
- Enum to jellybeans.vim constant red
- Incorporate jellybeans.vim `:hi Special` dark green

## [1.1.0] - 2022-09-05
### Added
- *Jellybeans+* variant
    - *Jellybeans+* is now the base theme, using mostly Dark+ based syntax
      highlighting
    - *Jellybeans.vim* is now a variant, including but building on *Jellybeans+*
      but with tweaks to bring more in line with vim (neovim & TreeSitter) based
      syntax highlighting
- Debug terminal colours
    - Terminal messages for info, error etc.
- Debugger language syntax based colours
    - Code/variable inspection: strings, constants etc.
### Changed
- *Jellybeans.vim* variant changes over *Jellybeans+*
    - True/False and other language constants -> `:hi Constant` red
    - Imports (C/C++ and python) to `:hi PreProc` light blue
    - Imported namespaces to foreground colour (e.g. C++ `std`, python `numpy`
      etc.)
    - Disable variable highlighting, except for method/function parameters
    - Python "self" keyword to `:hi Special` dark green

## [1.1.1] - 2022-09-30
### Added
- Language built-in primitives (`int` etc.) to `:hi Type` orange in *Jellybeans.vim*
  - This additional mapping is more true to vim. In VS Code Dark+ these are
    just grouped with other language keywords in `:hi PreProc` cyan
- `:hi StorageClass` brown for `storage.modifier` in *Jellybeans.vim*
- Add operator highlights (`=`, `<`, `*char`, etc.) from previous fg colour to
  `:hi PreProc` cyan, as in vim, in *Jellybeans.vim* variant only
  - Retained as fg colour in *Jellybeans+* to differentiate from the more
    widespread variable magenta highlights
- Semantic `macro` highlight to `Constant` red for *Jellybeans.vim*, emulates
  where C/C++ macros (ie. subject of `#define`) are used in neovim with
  TreeSitter highlight enabled.
  - Clashes with enum members, but this is true to vim
### Changed
- `debugTokenExpression.value` to a more legible suitable grey/blue
- 'Constant' variables and enummembers
  - Back to `:hi Special` green in *Jellybeans+*, more true to Dark+
  - Retain `:hi Constant` red for enummembers only in *Jellybeans.vim*,
    as in neovim
- String constant char escapes
  - From `StorageClass` brown to `Constant` red in *Jellybeans+*
  - From `StorageClass` brown to `Special` green in *Jellybeans.vim*, as in vim

## [1.1.2] - 2022-12-05
### Added
- *Jellybeans.vim* variant changes to closer match vim (neovim + TreeSitter) for some languages (C, C++, python):
  - Add C language punctuation and accessor colouring e.g.
    - Pointer access
    - Dot accessors
    - Function calls
    - Separators (commas)
    - Termination of statements
  - Add the same for C++ as above, including also:
    - All of C changes
    - Namespace and scope resolution
    - Arrow operator
  - Python changes, delimiters and punctuation e.g.
    - Class and function definitions terminators
    - Arg and parameter separators
    - Dot accessors
### Changed
- Support older VS Code versions
  - Change from minimum required vscode version 1.70 to 1.60
