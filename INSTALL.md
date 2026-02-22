# Install

Instructions for the AI agent. When the user asks to set up forge-text or troubleshoot their installation, follow these steps.

## Prerequisites Check

Before setup, verify the user has what they need:

1. **Git**: Run `git --version`. If missing, guide them:
   - Mac: "macOS will prompt you to install developer tools -- say yes"
   - Windows: "Download Git from git-scm.com/downloads/win -- keep all defaults during setup"
   - Linux: `sudo apt install git` or `sudo dnf install git`

2. **Rust** (for building deployment tools): Run `rustc --version`. If missing:
   - All platforms: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

3. **Claude Code** (or compatible tool): The user is already running it if they're talking to you.

## Build and Deploy

```bash
git submodule update --init lib   # initialize forge-lib (first time only)
make -C lib build                 # build Rust binaries (first time only)
make install                      # deploy 12 skills to all providers
make verify                       # confirm everything deployed
```

## Standalone Usage

If the user cloned forge-text directly:

```bash
git clone https://github.com/N4M3Z/forge-text.git
cd forge-text
git submodule update --init lib
make -C lib build
make install
```

Skills are immediately available as slash commands in Claude Code.

## As a Module

When used inside another forge project (e.g., forge-learn):

```bash
git clone https://github.com/N4M3Z/forge-text.git modules/forge-text
cd modules/forge-text && make install SCOPE=workspace
```

## Platform Notes

- **Windows**: Claude Code runs natively on Windows 10 (1809+). Requires [Git for Windows](https://git-scm.com/downloads/win) for shell operations.
- **Other tools**: Skills deploy to all providers via `make install`. Slash commands only work in Claude Code and compatible tools.
