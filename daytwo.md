# Day two

### Objectives

- Understand how to navigate and manipulate files via the Terminal.
- Learn key differences between `bash` and `zsh`.
- Practice essential commands for user support and troubleshooting.
- Get comfortable using `sudo` and exploring the fylesystem from the command line.

---

## Study materials

- [Apple - Terminal User Guide](https://support.apple.com/guide/terminal/welcome/mac)
- [SS64 = macOS Commands Reference](https://ss64.com/osx/)
- [zsh vs bash quick comparison](https://linuxhandbook.com/zsh-vs-bash/)

---

## Practical exercises

### Navigation & File Operations

  - **Basic**
- [ ] Open Terminal from Spotlight or Launchpad.
- [ ] Navigate to your home folder: `cd ~`.
- [ ] List all files (including hidden): `ls -la`.
- [ ] Create a folder named `terminal_practice`: `mkdir terminal_practice`.
- [ ] Create a file inside: `touch terminal_practice/test.txt`.
- [ ] Move and rename the file:
      `mv teterminal_practice/teste.txt terminal_practice/teste1.txt`
- [ ] Remove the file and directory:
      `rm terminal_practice/teste1.txt`
      `rmdir terminal_practice`

  - **Search files**
- [ ] Create a test folder structure with `.txt` and `.log` files.
- [ ] Use `find` to localize files by name:
      `find ~/Documents -name "*.log"`
- [ ] Use `grep` to search for words inside those files:
      `grep -i "error" ~/Documents/logs/*.log`

  - **File monipulation**
- [ ] Create a `.txt` with multiple text lines.
- [ ] Use `cat`, `less`, `head`, `tail` and `wc` to analyze it.
      `head -n 5 notes.txt`
      `tail -n 3 notes.txt`
      `wc -l notes.txt`

  - **Redirection and Pipe**
- [ ] Create an artificial logs with `echo` and redirection:
      `echo "Fake error log: $(date) >> test.log`
- [ ] Use `cat`, `grep`, `cut` and `sort` together:
      `cat test.log | grep "error" | cut -d ":" -f2 | sort

  - **Basic scripting**
- [ ] Let's make a very basic monitoring.sh to analyze our system!
      `#!/bin/zsh`
      `echo "Hello, $USER! Today is $(date)."`
      `...`
- [ ] Make it executable:
      `chmod +x monitoring.sh`
      `./monitoring.sh`

### Privilege escalation

- [ ] Run `whoami` and `id`.
- [ ] Try `sudo ls /var/root`.
      *(Note any password prompt behaviour)*
- [ ] Create a folder in `/User/Shared` using `sudo mkdir /Users/Shared/test_terminal`.

### System Info Commands

- [ ] `sw_vers` - OS version
- [ ] `uname -a` - kernel & system info
- [ ] `uptime` - how long the Mac has been on
- [ ] `system_profiler SPSoftwareDataType` - general software info

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
- Where are `zsh` customizations stored (`~/.zshrc`)? Are they auto-loaded?
- Why is `root` locked by default in macOS?
