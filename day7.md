# Day seven

### Objectives

- Get a general understanding of macOS security tools.
- Learn how macOS devices are managed remotely via MDM.

---

## Study materials

- [x] [Apple – Gatekeeper Overview](https://support.apple.com/en-us/HT202491)
- [x] [Apple Platform Security Guide (PDF)](https://support.apple.com/guide/security/welcome/web)
- [x] [Apple Business Manager – MDM Overview](https://support.apple.com/guide/apple-business-manager/welcome/web)

---

## Practical exercises

### Security Tools

- [x] Check if **FileVault** is enabled:
  - Go to **System Settings > Privacy & Security > FileVault**
  - Or via Terminal:
    - fdesetup status

- [x] Check Gatekeeper status:
  - spctl --status
- [x] Check if system is enrolled in MDM and list configuration profiles:
  - profiles status -type enrollment
  - profiles list

### Research task

- [x] Visit the websites for Jamf or Mosyle.
- [x] Note 3 core features of either platform (device management, app deployment, security compliance).

---

## Notes

### Concepts

- **Gatekeeper** ensures only trusted apps (App Store or notarized by Apple) can run.
- **FileVault** encrypts the entire disk and protects data at rest.
- **MDM (Mobile Device Management)** allows IT admins to configure and control devices remotely.

### Real-world relevance

- As a Technical Support Specialist, knowing how to check MDM enrollment and security status is essential for onboarding, compliance, and troubleshooting.
- Tools like Jamf and Mosyle are used daily in enterprise environments to manage software updates, enforce security policies, and deploy configurations remotely.

---
