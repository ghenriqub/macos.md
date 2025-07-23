# Day two

### Objectives

- Understand how to navigate and manipulate files via the Terminal.
- Learn key differences between `bash` and `zsh`.
- Practice essential commands for user support and troubleshooting.
- Get comfortable using `sudo` and exploring the fylesystem from the command line.

---

## Study materials

- [x] [Apple - Terminal User Guide](https://support.apple.com/guide/terminal/welcome/mac)
- [x] [SS64 = macOS Commands Reference](https://ss64.com/osx/)
- [x] [zsh vs bash quick comparison](https://codeparrot.ai/blogs/zsh-vs-bash-key-differences-features-and-which-one-to-choose)

---

## Practical exercises

### Navigation & File Operations

  - **Basic**
- [x] Open Terminal from Spotlight or Launchpad.
- [x] Navigate to your home folder: `cd ~`.
- [x] List all files (including hidden): `ls -la`.
- [x] Create a folder named `terminal_practice`: `mkdir terminal_practice`.
- [x] Create a file inside: `touch terminal_practice/test.txt`.
- [x] Move and rename the file:
      `mv terminal_practice/teste.txt terminal_practice/teste1.txt`
- [x] Remove the file and directory:
      `rm terminal_practice/teste1.txt`
      `rmdir terminal_practice`

  - **Search files**
- [x] Create a test folder structure with `.txt` and `.log` files.
- [x] Use `find` to localize files by name:
      `find ~/Documents -name "*.log"`
- [x] Use `grep` to search for words inside those files:
      `grep -i "error" ~/Documents/logs/*.log`
- [x] Remove the entire directory
      `rm -r terminal_test`

  - **File manipulation**
- [x] Create a `.txt` with multiple text lines.
- [x] Use `cat`, `less`, `head`, `tail` and `wc` to analyze it.
      `head -n 5 notes.txt`
      `tail -n 3 notes.txt`
      `wc -l notes.txt`

  - **Redirection and Pipe**
- [x] Create an artificial logs with `echo` and redirection:
      `echo "Fake error log: $(date)" >> test.log`
- [x] Use `cat`, `grep`, `cut` and `sort` together:
      `cat test.log | grep "error" | cut -d ":" -f2 | sort`

  - **Basic scripting**
- [x] Let's make a **monitoring.zsh** to analyze our system with a security focus!
      `#!/bin/zsh`
      `# macOS Monitoring Report`
      `...`
- [x] Make it executable:
      `chmod +x monitoring.zsh`
      `./monitoring.zsh`

### Privilege escalation

- [x] Run `whoami` and `id`.
- [x] Try `sudo ls /var/root`.
      *(Note any password prompt behaviour)*
- [x] Create a folder in `/User/Shared` using `sudo mkdir /Users/Shared/test_terminal`.

### System Info Commands

- [x] `sw_vers` - OS version
- [x] `uname -a` - kernel & system info
      wtf is `Darwin`?
- [x] `uptime` - how long the Mac has been on
- [x] `system_profiler SPSoftwareDataType` - general software info

---

## Notes

### Observations

- macOS uses `zsh` by default since Catalina (10.15), but `bash` is still available.
- The filesystem is case-sensitive but not case-insistent in Finder.
- `sudo` behaviour is cached - no password is required again for a short time.
- `man` pages are available for almost everything.
  Try: `man sw_vers`, `man mkdir`, `man sudo`.

---

### Common questions

- How does macOS handle PATHs differently for user vs root shells?
  - macOS treats the `PATHs` differently between standard users and root for security and previsibility reasons.
    For regular users, the `PATH` is mounted based in various files, like: `/etc/paths`, `/etc/paths.d/*`.
    For sudo users, it's restricted: `/usr/bin:/bin:/usr/sbin:/sbin`. It avoids malicious commands with high priviledge in `/usr/local/bin` or in `~/bin`.
- Where are `zsh` customizations stored (`~/.zshrc`)? Are they auto-loaded?
  - If interactive, it is! We also built ours, its the .zshrc file in the root of this repo.
- Why is `root` locked by default in macOS?
  - Guess what... Security! It avoid malicious direct logins as root. The user exists, it's just kept with the password unenabled (`!` in `/etc/master.passwd`), being able to work only when necessary.
