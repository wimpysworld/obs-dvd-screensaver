<h1 align="center">
  <img src="./data/dvd.png" alt="DVD Screen Saver">
  <br />
  DVD Screen Saver
</h1>

<p align="center"><b>A plugin for OBS Studio that adds a DVD style screen saver source 📀</b><i>Will it hit the corner?</i></p>

# DVD Screen Saver

This is a plugin for [OBS Studio](https://obsproject.com/) that adds a new 
source type that can turn any image into a DVD style screen saver. Use it just
for fun, or make your "back soon" scene more interesting, perhaps use it as a
channel point redemption or when you need to watermark your your live stream
with a moving image 🛡️

## Requirements

- OBS Studio 31.0.0 or newer

## Building from Source

You'll need CMake 3.28+, a C compiler, and the OBS Studio development libraries. See the [OBS Plugin Template](https://github.com/obsproject/obs-plugintemplate) for detailed environment setup.

**Linux:**
```bash
cmake --preset ubuntu-x86_64
cmake --build --preset ubuntu-x86_64
```

**Windows:**
```bash
cmake --preset windows-x64
cmake --build --preset windows-x64
```

**macOS:**
```bash
cmake --preset macos
cmake --build --preset macos
```

A Nix flake is available for development: `nix develop`

## History

It is the continuation of the original [dvds3](https://github.com/univrsal/dvds3)
plugin by [univrsal](https://github.com/univrsal), inspired by
[some patches](https://github.com/Ayowel/dvds3/commit/c177440488d716e950bbb042654d9de1f18fffdc)
by [Ayowel](https://github.com/Ayowel) and all wrapped up in the
[OBS Plugin Template](https://github.com/obsproject/obs-plugintemplate) so that
it builds 🧱 from source against current versions of OBS Studio.

**This project is only tested on Linux 🐧**.
It is built and released for Windows 🪟 and macOS 🍏 and should work fine, if it doesn't patches are welcome 🩹