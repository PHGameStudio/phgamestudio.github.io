---
layout: default
title: Guide to Setup Basic Terminal Development Environment
permalink: /resources/terminal-guide/
---

# Guide to Setup Basic Terminal Development Environment

## Setup Package Manager

### Windows

- Winget should be pre-installed on new windows versions
- On old windows 10, install "App Installer" from microsoft store
- Verify that it works by typing `winget` in powershell

### Mac OS

- Install homebrew following instructions on [brew.sh](https://brew.sh)
- Pay attention to the final few lines of output when installing homebrew, these need to be run manually

### Linux (Immutable Distros)

- Install homebrew
- Since GUI apps from homebrew don't work on Linux, use flatpak for them, use homebrew over flatpak for command line programs

## Install Your Terminal

### Windows

- Use Windows Terminal
- Run `winget install --id Microsoft.WindowsTerminal -e` in powershell
- Launch from start menu

### Mac OS and Linux

- Use Kitty terminal
- Mac OS: search for "terminal" in spotlight/launchpad and open, run `brew install --cask kitty`, launch kitty from spotlight/launchpad
- Linux: use distro's native package manager or `rpm-ostree` (no flatpak package)
	- Or use the official binary installer: `curl -L https://sw.kovidgoyal.net/kitty/installer.sh | sh /dev/stdin` (not recommended, only use this if all other methods aren't available)

## Basic commands

- `ls`: **l**i**s**ts contents in the current working directory
- `pwd`: **p**rints the path of the current **w**orking **d**irectory
- `cd path/to/directory`: **c**hanges working **d**irectory to `path/to/directory`
- `mkdir directory-name`: **m**a**k**es a **dir**ectory named `directory-name`
- When using a path containing special symbols like spaces in commands, wrap the entire path in quotes or escape the spaces like `path/to/directory\ with\ spaces` (only on Mac OS or linux)

### What Are Paths (by Claude)

A **path** is an address that tells the computer exactly where a file, folder, or program is located in the file system. There are two types of paths and an important environment variable to understand:

#### File Paths

**Absolute Paths**
- Complete addresses that specify the full location from the top of the file system
- Unix/Linux/macOS example: `/Users/Twilio/GitHub/scripts/file.sh`
- Windows example: `C:\ProgramFiles\CompanyA\file.exe`
- Always work regardless of current location

**Relative Paths**
- Addresses that depend on the current working directory
- Use special symbols to navigate: `.` (current directory), `..` (parent directory), `~` (home directory)
- Example: `../../folder/file.txt` means "go up two directories, then down into folder"

**Path Separators**
- Unix-like systems use forward slashes: `/home/user/documents`
- Windows uses backslashes: `C:\Users\Documents`

#### PATH Environment Variable

**What It Does**
- A list of directories the command line searches when running commands
- Allows typing commands like `mkdir` instead of the full path like `/usr/bin/mkdir`
- Directories are separated by colons on Unix (`:`) and semicolons on Windows (`;`)

**Why It Matters**
- Programs in PATH directories can be run from anywhere without specifying their location
- Order matters—the first matching program found is the one that runs
- To run programs not in PATH, provide the full path or use `./` prefix for current directory

## Setup A Terminal File Manager So That You Don't Need To Use The Basic Commands

- Install the [yazi](https://yazi-rs.github.io/) terminal file manager
	- Windows: `winget install sxyazi.yazi`
	- Mac OS: `brew install yazi`
	- Linux: use native package manager or same as Mac OS
- Setup the shell wrapper according to the [official guide](https://yazi-rs.github.io/docs/quick-start/)
- Type `y` in the terminal to enter an explorer-like interface, use hjkl or arrow keys to move, and type `q` to quit. Terminal working directory automatically changes to the directory in yazi before quitting

## Editing Text Using Terminal

- Use the `msedit` editor
	- Windows: `winget install Microsoft.Edit`
	- Mac OS: `brew install msedit`
	- Linux: use native package manager or same as Mac OS
- Edit files using the command `msedit path/to/file`
- Keyboard shortcuts same as most text editors like notepad, textedit, and vscode
