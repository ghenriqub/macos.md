# Day three

### Objectives

- Understand the macOS filesystem hierarchy.
- Learn how file and folder permissions work in macOS.
- Practice using `chmod` and `chown` to customize permissions.
- Navigate key system folders through Finder and Terminal.

---

## Study materials

- [x] [Apple – File System Overview](https://support.apple.com/guide/mac-help/macos-file-system-mchlp1140/mac)
- [x] [SS64 - chmod](https://ss64.com/osx/chmod.html)
- [x] [SS64 - chown](https://ss64.com/osx/chown.html)
- [x] [Mac Terminal Permissions Guide - MakeUseOf](https://www.makeuseof.com/tag/mac-terminal-permissions/)

---

## Practical exercises

### Filesystem hierarchy

- [x] Open Finder and use `Cmd + Shift + G` to navigate to:
  - `/System`
  - `/Library`
  - `/Users`
- [x] Do the same using the Terminal:
  - `cd /System`
  - `cd /Library`
  - `cd /Users`
- [x] Try creating files or folders in those locations (expect permission denied).

### Permissions basics

- [x] Create a new folder and file for testing:
  - `mkdir ~/permissions_test`
  - `touch ~/permissions_test/test.txt`
- [x] Check its default permissions:
  - `ls -l ~/permissions_test/test.txt`

### Customizing permissions

- [x] Use `chmod` to remove read permissions for others:
  - `chmod o-r ~/permissions_test/test.txt`
- [x] Use `chmod` to add execute permissions for the user:
  - `chmod u+x ~/permissions_test/test.txt`
- [x] Use symbolic and octal modes:
  - `chmod 755 ~/permissions_test/test.txt`
  - `chmod u=rwx,g=rx,o=rx ~/permissions_test/test.txt`

### Changing ownership

- [x] Run `whoami` and `id` to confirm your current user.
- [x] Use `chown` to change the owner of the test file to `root`:
  - `sudo chown root ~/permissions_test/test.txt`
- [x] Use `ls -l` to confirm ownership change.

### Cleanup

- [x] Reset ownership and permissions:
  - `sudo chown $USER ~/permissions_test/test.txt`
  - `chmod 644 ~/permissions_test/test.txt`
- [x] Remove the test directory:
  - `rm ~/permissions_test/test.txt`
  - `rmdir ~/permissions_test`

---

## Notes

### Observations

- `/System` is read-only under SIP (System Integrity Protection). Even `sudo` can’t modify it unless SIP is disabled.
- `/Library` contains system-wide preferences and resources. It's writable with `sudo`.
- `/Users` is where user directories live, and regular users have write access to their own home folders.
- `chmod` uses both **symbolic (u/g/o + r/w/x)** and **octal (e.g., 755, 644)** modes.
- `chown` requires elevated privileges to transfer ownership to another user.

### Common questions

- Why can’t I edit files in `/System` even as `root`?
  - Because of SIP (System Integrity Protection). It restricts even root from modifying protected areas unless SIP is disabled via Recovery Mode.
- What does `chmod 755` mean in plain English?
  - User can read/write/execute, group and others can read/execute only.
- Can I use `chmod` and `chown` from Finder?
  - No direct interface, but Finder reflects permission changes. For GUI-level changes, use `Get Info (⌘+I)` and modify Sharing & Permissions at the bottom.
- Why are permissions important in support tasks?
  - Many user issues stem from incorrect permissions, especially after migrations, script failures, or manual file moves.

---
