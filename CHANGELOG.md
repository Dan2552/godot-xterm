# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).


## [Unreleased]
[Unreleased]: https://github.com/lihop/godot-xterm/compare/v2.0.0...HEAD
### Added
- Basic readline utility that provides line editing capabilities similar to GNU Readline.

### Removed
- TerminalSettings resource. Not currently used, and was showing up in every 'new resource' menu that is displayed after clicking on an empty Resource slot.


## [v2.0.0] - 2021-07-25
[v2.0.0]: https://github.com/lihop/godot-xterm/compare/v1.2.1...v2.0.0
### Added
- Terminal editor plugin. Adds integrated terminal to Godot editor.
- Xresources import plugin.
- [#39][i39]: Support for the bell "\u0007" character.
- HTML5 Support.
- [#24][i24]: Support for Windows 32-bit (Terminal node only).

### Changed
- [#44][i44]: Default theme to match Godot's default theme.
- Supported Godot version -> 3.3.2.
- Set a default theme if no theme property has been set.
- Changed default font from Cousine to Hack, which is the same as Godot's script editor, and reduced size from 16 to 14.
- TPut no longer registered as a unique global class (i.e. removed `class_name TPut`).

### Fixed
- [#40][i40]: Vim related bugs, caused by incorrectly handled control sequences.
- Don't swap red and blue channels of theme colors.
- Use "Light Cyan" color from theme. Previously ignored.

[i24]: https://github.com/lihop/godot-xterm/issues/24
[i39]: https://github.com/lihop/godot-xterm/issues/39
[i40]: https://github.com/lihop/godot-xterm/issues/40
[i44]: https://github.com/lihop/godot-xterm/issues/44


## [v1.2.1] - 2020-11-23
[v1.2.1]: https://github.com/lihop/godot-xterm/compare/v1.2.0...v1.2.1
### Changed
- GitHub Actions workflow now produces both a release and debug zip archive.

### Fixed
- Release binary for Windows 64-bit export.


## [v1.2.0] - 2020-11-21
[v1.2.0]: https://github.com/lihop/godot-xterm/compare/v1.0.0...v1.2.0
### Added
- Support for macOS 64-bit including Pseudoterminal.
- Partial support for Windows 64-bit and compiling on Windows using MSVC. Pseudoterminal not yet supported. 32-bit builds might be possible but not yet built/tested.

### Changed
- Updated build script. On Linux `./build.sh` will create a debug build of the gdnative library for the current platform.
- Removed all pre-compiled binaries using BFG [Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/), thus re-writing git history.

### Fixed
- Fixed bug where incorrect data would sometimes be written to the terminal when passing a string to the Terminal's `write()` method.
- Positioned background rect at 0,0 so it is no longer offset if a margin is added when Terminal is a child of a Container node.
- Passed correct argv to the execvp call of Pseudoterminal. Previously argv[0] was not set to the program's name which caused the Pseudoterminal node not to work on macOS with the zsh shell.


## [v1.0.0] - 2020-10-05
[v1.0.0]: https://github.com/lihop/godot-xterm/releases/tag/v1.0.0
### Added
- Changelog.
- Asciicast importer plugin. Enables the import of .cast ([asciicast files v2](https://github.com/asciinema/asciinema/blob/master/doc/asciicast-v2.md)) that can be made using the [asciinema](https://asciinema.org/) terminal session recorder. See the [asciicast scene](/examples/asciicast) for example usage.
- Pre-built binary for x11 platform.

### Changed
- Implementation of Terminal node from GDScript to GDNative using [Aetf's patched version of libtsm](https://github.com/Aetf/libtsm).
- Move input handling to the Terminal node itself, rather than handling it in a seperate Control node.
- The Terminal `write()` method now accepts both String and PoolByteArray.
