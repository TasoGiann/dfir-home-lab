# Lessons Learned

## 2026-04-24 — Lab Setup Day 1

### VirtualBox Host-Only Network Driver Failure
**Problem:** Could not create host-only network. Error: E_FAIL 0x80004005,
"Could not find Host Interface Networking driver."
**Root cause:** VirtualMachinePlatform (required by WSL2) conflicts with
VirtualBox's host-only network driver on Windows 11.
**Fix:** Switched to NAT Network instead of host-only. NAT Network provides
VM-to-VM connectivity without requiring the host network driver.
**Lesson:** Read error codes before reinstalling. The error pointed to a
driver conflict, not a broken installation.

### Parrot sudo Password Unknown
**Problem:** sudo password for user tasos not working after VM was created.
**Root cause:** User was never added to sudoers, or password was set
incorrectly during installation.
**Fix:** Used pkexec passwd tasos to reset password without requiring
existing sudo access.
**Lesson:** Always verify sudo works immediately after creating a Linux VM.
Document the password somewhere secure.

### Windows Unattended Install Creates Non-Admin User
**Problem:** VirtualBox unattended install created user with no admin rights.
UAC prompts had no Yes button, only credential fields with no input available.
**Fix:** Reinstalled Windows manually (unchecked unattended install) to
control account creation.
**Lesson:** Always uncheck unattended installation when creating Windows VMs
in VirtualBox. Manual install takes 15 minutes and avoids hours of admin
access troubleshooting.

## 2026-04-29 — Lab Setup Day 2

### Sysmon Install Requires Admin PowerShell
**Problem:** Sysmon install failed with "You need to launch Sysmon as Administrator."
**Root cause:** PowerShell was open but not elevated.
**Fix:** Right-click Start > Terminal (Admin) before running Sysmon installer.
**Lesson:** Always verify the title bar says "Administrator:" before running any security tooling installs on Windows.

### Nested Zip Extraction Creates Double Folder
**Problem:** sysmon-config-master.zip extracted to sysmon-config-master\sysmon-config-master\
causing the XML path to be wrong.
**Fix:** Used ls to find the actual path before running the install command.
**Lesson:** Always verify extracted folder structure before referencing paths in commands.
