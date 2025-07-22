# Day one

### Objectives

- Get familiar with the macOS graphical interface.
- Learn how to switch between users and configure system settings.
- Identify key differences between macOS and other systems (Linux/Windows).
- Begin building intuition as a technical support professional, not just a regular user.

---

## Study links

- [x] [Apple - support](https://support.apple.com/mac)
- [x] [Keyboard Shortcuts](https://support.apple.com/en-us/HT201236)

---

## Practical Exercises

### User Accounts

- [ ] Create two user accounts:
  - One **administrator**
  - One **Standard user**
- [ ] Switch between users and compare permissions.

### Interface Exploration

- [x] Customize the Dock (add/remove/reorder apps).
- [x] Open Finder and:
  - Show sidebar
  - Show hidden files: `Cmd + Shift + .`
- [x] Create a new Desktop Space with **Mission Control**.
- [x] Use Launchpad to open apps.     

### System Settings / Settings

- [x] Change the desktop wallpaper.
- [x] Enable or disable "auto-hide Dock".
- [x] Enable **Dark Mode**
- [x] Log out using `Cmd + Shift + Q`, then log back in.

### Spotlight Search

- [x] Use `Cmd + Space` to:
  - Launch an app (Terminal).
  - Search for system settings.
  - Find a file in your home directory.

---

## Notes

### Observations

- Differences between admin and standard users:
  - Admin:
    - they have permissions to change system settings and install software for all users.
    - they can unlock the padlock icon in `**System Settings** -> **Users & Groups**, **Security & Privacy**, etc.
    - they can also use `sudo` in the terminal (by default, the first user created has this access).
    - per consequence, they have access to the `admin` group.
  - Standard users:
    - by default they can't use `sudo` directly (except if configured by `/etc/sudoers`).
    - can install apps in user level (`~/Applications`), but not in `/Applications`.
    - they can't change system settings that affect all users.

```zsh
groups $(whoami)
```
> A lot of installation problems or configurations in companies happen because the user is like "standard" and tries to install corporate software. **Solution**: installation through **MDM**, remote `sudo` or adjust permitions for that user.

- Default folder structure under `/Users`:

Each user has their own folder in `/Users/<username>`, with the following structure:

```zsh
/Users/johndoe/
├── Applications/     # Apps only for this user
├── Desktop/          # Desktop
├── Documents/        # Documents
├── Downloads/        # Downloads
├── Library/          # Settings and data from apps (hidden)
├── Movies/           # Videos
├── Music/            # Musics
├── Pictures/         # Images
├── Public/           # Shared folder
└── Sites/            # (Obsolete - used in older versions for local websites)
```

> The `Library` dir is hidden by default, but will be crucial for troubleshooting!!!
> To access, press `Cmd + Shift + .` or `Go -> Go to Folder -> ~/Library`.

- New behaviors compared to Linux/Windows:
  - App installation: `.app` bundles are placed in `/Applications`.
  - Libraries: `~/Library` / `/Library`.
  - Filesystem: APFS (with snapshots and containers).
  - Window manager: Mission Control / Spaces.
  - Standard terminal: Zsh (`/bin/zsh`).
  - Disk permitions: Gatekeeper + SIP + ACLs

> **SIP (System Integrity Protection)** prevents the access/modification in `/System`, `/bin`, `/sbin`, `/usr` (except `/usr/local`) even with `sudo`.
> To disable **SIP** you must boot into Recovery Mode and use the Terminal.

- Why does `~/Library` behave differently depending on the app/user:

The `~/Library` holds preferences, caches, and app support for that user.

  - Why the variable behaviour:
    - **Sandboxing**: apps from AppStore **can't** freely access files outside their "containers" in `~/Library/Containers/`.
    - **iCloud Sync**: can synchronize part of the `Library`, like `Mobile Documents`.
    - **Specific permissions**: some apps save preferences in `~/Library/Preferences/`, others in sub-folders or using SQLite.
    - **Automatic fallback**: if the app doesn't have permition to write to `/Library` (global), it will try `~/Library` instead (local).

  - Example:
    - `~/Library/Preferences/com.apple.finder.plist`: Finder's preferences for that user.
    - `~/Library/Application Support/`: data saved by apps (Firefox, VSCode, etc.).
    - `~/Library/Caches/`: temporary cache (can be safely deleted).

- How does Mission Control relate to Spaces/desktops under the hood:

**Mission Control** is the graphic interface to manipulate:

   - **Spaces** (virtual Desktops).
   - **Full-screen apps** (each fullscreen app creates its own Space).
   - **Split View apps** (two apps side-by-side in one Space).

  - How it works internally:
    - Each Space is a managed instance handled by the **WindowsServer**.
    - Spaces are represented as "virtual desktops" at the graphic compositor level.
    - `Dock.app` and `SystemUIServer` control animations, transitions and window mapping between Spaces.

  - For Technical Support:
    - Users who "lose windows" have often just switched Spaces.
    - `Ctrl + arrow` or `Mission Control (F3)` is enough.
---

## Summary

> "Every click has a shortcut. Every shortcut has a CLI equivalent."

Today’s focus was GUI-based, but we’re already laying the foundation for fast support troubleshooting. Let's think like a user *and* like a sysadmin. The mindset shift started.
