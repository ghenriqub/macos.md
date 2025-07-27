# Day four

### Objectives

- Understand how to install and manage macOS applications via Homebrew.
- Practice using Homebrew to install, update, and remove packages.
- Troubleshoot installations with `brew doctor`.

---

## Study materials

- [x] [Homebrew - Official Site](https://brew.sh/)
- [x] [Homebrew - Manpage](https://docs.brew.sh/Manpage)

---

## Practical exercises

### Install & Configure Homebrew

- [x] Open Terminal and install Homebrew:
  - `/bin/bash -c ...`
- [x] Confirm installation:
  - `brew --version`
- [x] Run diagnostics:
  - `brew doctor`
- [x] Update formulas and Homebrew itself:
  - `brew update`

### Package management:

- [x] Install CLI tools:
  - `brew install htop wget tree`
- [x] Run the apps to verify installation:
  - `htop`
  - `wget --version`
  - `tree --version`
- [x] Uninstall a package:
  - `brew uninstall tree`
- [x] Search for available packages:
  - `brew search <package>`
- [x] Check info and dependencies:
  - `brew info wget`
- [x] List all installed packages:
  - `brew list`
- [x] Clean up versions and cache:
  - `brew cleanup`

---

## Notes

### Observations

- Homebrew installs software to `/opt/homebrew/` on Apple Silicon, or `/usr/local/` on Intel Macs.
- Installed binaries are symlinked to `/opt/homebrew/bin` (or `/usr/local/bin`), which should be in our `$PATH`.
- `brew doctor` is helpful to detect common environment issues.
- Some GUI apps can be installed via `brew install --cask`.

### Common questions

- Whats the difference between `brew install` and `brew install --cask`?
  - `brew install` is for CLI tools. `--cask` installs GUI apps (Firefox, Slack, etc).
- Where are installed files located?
  - They are installed under `/opt/homebrew/Cellar` (or `/usr/local/Cellar`), with symlinks to `/opt/homebrew/bin`.
- Can I upgrade all apps at once?
  - Just `brew upgrade` everything.
- How can I see what is outdated?
  - Just check with `brew outdated`.

---
