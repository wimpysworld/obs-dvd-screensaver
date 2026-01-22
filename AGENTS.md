# AGENTS.md

OBS Studio plugin that adds a DVD-style bouncing screensaver source. Turns any image into a bouncing logo with colour shift on each bounce.

## Tech stack

- **Language:** C (single source file)
- **Build:** CMake 3.28+, CMakePresets for cross-platform
- **Dependencies:** libobs (OBS Studio 31.0.0+)
- **Dev environment:** Nix flake (clang-tools, cmake, cmake-format)

## Project structure

```
src/plugin-main.c    # All plugin logic
data/                # Assets (dvd.png, locale)
cmake/               # Build helpers
.clang-format        # C code style (clang-format 16+)
.gersemirc           # CMake formatting
buildspec.json       # Version, dependencies, metadata
```

## Build commands

Linux:

```bash
cmake --preset ubuntu-x86_64
cmake --build --preset ubuntu-x86_64
```

Windows:

```bash
cmake --preset windows-x64
cmake --build --preset windows-x64
```

macOS (currently disabled in CI):

```bash
cmake --preset macos
cmake --build --preset macos
```

## Development environment

Enter Nix shell for dependencies:

```bash
nix develop
```

## Code style

- **C formatting:** clang-format 16+, 8-space tabs, 120 column limit
- **CMake formatting:** gersemi, 2-space indent, 120 line length
- **Naming:** Settings prefixed `S_`, localised text prefixed `T_`
- **Structure:** OBS plugin API patterns with `obs_source_info` struct

Format before committing:

```bash
clang-format -i src/plugin-main.c
gersemi -i CMakeLists.txt
```

## Architecture notes

Single-file plugin implementing:

- `dvd_source_info` struct registered via `obs_register_source()`
- `dvd_source_tick()` handles bounce physics and colour shift
- `dvd_source_render()` draws scaled image at current position
- Colour filter disabled on macOS (`#ifndef MAC_OS` guards)

## Constraints

- OBS Studio 31.0.0+ required
- macOS builds currently disabled in CI
- Primarily tested on Linux
- Colour shift feature unavailable on macOS
