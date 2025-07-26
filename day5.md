# Day five

### Objectives

- Understand how macOS manages network interfaces and energy settings.
- Use Terminal tools to inspect and manipulate network and power configurations.
- Learn where and how to switch network locations for troubleshooting and flexibility.

---

## Study materials

- [ ] [Apple - `networksetup` Command Manual]()
- [ ] [Apple - `pmset` Manual Page]()

---

## Practical exercises

### Network Management

- [ ] List all hardware ports (including Wi-Fi and Ethernet)
  - `networksetup -listallhardwareports
- [ ] Get current IP address of Wi-Fi interface (`en0`)
  - `ipconfig getifaddr en0`
- [ ] Get DNS servers for active service
  - `networksetup -getdnsservers Wi-Fi
- [ ] Get current network location
  - `scselect`
- [ ] Create a new network location manually
  - Open **System Preferences > Network > Location > Edit Locations**
  - Add a new location (e.g., `TestLocation`) and apply changes
- [ ] Switch between locations
  - From GUI: **Apple menu > System preferences > Network > Location**
  - From Terminal:
    - `scselect TestLocation`

### Power Management

- [ ] View current power settings
  - `pmset -g`
- [ ] View battery status
  - `pmset -g batt`
- [ ] View scheduled power events
  - `pmset -g sched`
- [ ] Set display sleep time (e.g. 5 minutes on battery)
  - `sudo pmset -b displaysleep 5`
- [ ] Restore default settings
  - sudo pmset restoredefaults

---

## Notes

### Observations

- `networksetup` allows granular control over interfaces, DNS, proxies, and more. Requires root for many actions.
- The `en0` interface usually refers to Wi-Fi on Macs, but it may vary depending on hardware.
- `pmset` gives deep insight into power behaviors - sleep, hibernation, wake triggers, etc.
- macOS separates energy settings between battery (`-b`), charger (`-c`), and UPS (`-u`).

### Common questions

- What is a "location" in macOS networking?
  - A set of network preferences and configurations you can switch between. Useful for toggling between home, office, or public settings.
- How does macOS decide which network to use first?
  - It uses service order priority, which can be changed in **System Preferences > Network > Gear Icon > Ser Service Order**.
- What's the difference between `pmset -g` and `pmset -g batt`?
  - `pmset -g` shows global power settings. `pmset -g batt` shows battery charge info and current power source.
- Can I schedule wake/sleep with `pmset`?
  - Yes, but it requires root and is limited in the GUI, use:
    - `sudo pmset repeat wakeorpower on MTWRFSU 08:00:00`

---
