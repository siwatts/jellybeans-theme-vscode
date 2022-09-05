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
