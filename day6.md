# Day six

### Objectives

- Learn to diagnose performance issues, disk usage problems, and system slowdowns.
- Understand how to read system logs and monitor key metrics like CPU and memory usage.

---

## Study materials

- [x] Explore **Activity Monitor** (CPU, Memory, Disk tabs)
- [x] [Apple – Console.app Overview](https://support.apple.com/guide/console/welcome/mac)
- [x] Learn how to use the `top` command in Terminal

---

## Practical exercises

### System Monitoring

- [x] Open **Activity Monitor** and identify the process using the most CPU.
- [x] Switch to the **Memory** tab and sort by memory usage.
- [x] Use the `top` command in Terminal to view real-time system processes:
  - `top -o cpu`
- [ ] Monitor disk usage using the Disk tab in Activity Monitor.

### Logs and Diagnostics

- [ ] Open Console.app from /Applications/Utilities/.
  - Use the search bar and filter for `"error"` or `"fault"`.
  - Identify a recent system error and write it down.
- [ ] Inspect the system.log:
  - `sudo less /var/log/system.log`

---

## Notes

### Observations

- Activity Monitor is like a GUI wrapper for `top` and `ps`, but with visual charts and process tree.
- In Console.app, most app-level logs appear under "All Messages". You can also browse crash reports.
- `/var/log/system.log` is especially useful when diagnosing login failures, kernel panics, or power events.

### Troubleshooting checklist

- High CPU usage
  - Identify background processes or runaway apps.
- Memory pressure high
  - Look for memory leaks or browser tabs eating RAM.
- Disk
  - Check for heavy read/write processes (Time Machine, Spotlight indexing).

---
