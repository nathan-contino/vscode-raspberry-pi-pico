# Raspberry Pi Pico Visual Studio Code extension

> NOTE: The extension is still under development.

This is the official Visual Studio Code extension for Raspberry Pi Pico development. It provides a set of tools to help you getting started with development for the Pico boards using Visual Studio Code and the official [Pico-SDK](https://github.com/raspberrypi/pico-sdk).

[Download latest Beta RC 📀](https://github.com/paulober/vscode-raspberry-pi-pico/releases/tag/0.12.0)

## Features

- Project generator (targets ninja build-system)
- Automatic CMake configuration on project load
- Easy option to switch between different versions of the Pico-SDK and tools
- No configuration of environment variables required
- Automatic download/management of Toolchain and SDK and some tools (no separate manuall download/installation required)
- On-click project compilation per status bar button (with the selected Pico-SDK and tools)
- Offline documentation for the Pico-SDK

## Requirements by OS

> Supported Platforms: Windows x64, macOS (Sonoma and newer only), Linux x64 and arm64

- Visual Studio Code v1.87.0 or later

### macOS
All requirements for macOS can be installed by running `xcode-select --install` from Terminal
- Git (in PATH)
- Tar (in PATH)
- Native C/C++ compiler (in PATH), supported compilers are: `gcc` and `clang`

### Raspberry Pi OS
All requirements for Raspberry Pi OS can be installed by running `sudo apt install openocd ninja-build`

### Linux
- Python 3.9 or later (in PATH or set in settings)
- Git (in PATH)
- Tar (in PATH)
- Native C/C++ compiler (in PATH), supported compilers are: `gcc` and `clang`
- Ninja in PATH (arm64 only)
- \[Optional\] OpenOCD for debuging (Raspberry Pi OS only)

## Extension Settings

This extension contributes the following settings:

* `raspberry-pi-pico.cmakePath`: Set custom cmake path
* `raspberry-pi-pico.python3Path`: Set custom python3 path
* `raspberry-pi-pico.ninjaPath`: Set custom ninja path
* `raspberry-pi-pico.gitPath`: Set custom git path
* `raspberry-pi-pico.cmakeAutoConfigure`: Enable/Disable cmake auto configure on project load
* `raspberry-pi-pico.githubToken`: Takes a GitHub personal access token (classic) with the `public_repo` scope. It is used to check GitHub for available versions of the Pico SDK and other tools. Without one, the extension will use the GitHub API unauthenticated, which has a much lower rate limit causing many features to not work properly if the limit is reached.

## Known Issues

- Custom Ninja, Python3 or git paths are not stored in CMakeLists.txt like SDK and Toolchain paths so using them would require to build and configure the project thought the extension

### GitHub API Rate Limit ("Error while retrieving SDK and toolchain versions")

If the extension fails to get available Pico SDK versions, it might be because of the GitHub API rate limit. You can create a personal access token (classic) with the `public_repo` scope and set it in the global ("User" not "Workspace") extension settings to increase the rate limit.
