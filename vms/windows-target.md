# Windows-Target VM

## Specifications
- OS: Windows 11 Enterprise Evaluation (Build 26100)
- RAM: 5120 MB
- CPUs: 4
- Disk: 80 GB
- Hypervisor: VirtualBox
- Network: dfir-lab NAT Network (10.0.2.0/24)
- IP: 10.0.2.3 (DHCP)
- Hostname: DESKTOP-VI4V2P8
- Local user: tasos (Administrator)

## Purpose
Primary investigation target. Represents a standard enterprise
Windows endpoint. Used for:
- Generating forensic artifacts for analysis practice
- Simulating attack scenarios
- Practicing Windows IR triage and artifact collection

## Installed Tools
- Sysmon v15.20 (SwiftOnSecurity config)
- VirtualBox Guest Additions

## Logging Configuration
- Sysmon: enabled, logging to Microsoft-Windows-Sysmon/Operational
- PowerShell Script Block Logging: enabled
- Process Creation Audit: enabled with command line
- Event log location: C:\Windows\System32\winevt\Logs\

## Snapshots
- 01-clean-install: Fresh Windows 11, local admin account created
- 02-sysmon-and-logging-configured: Sysmon + audit policy enabled
- 03-baseline-captured: Clean baseline CSV files captured

## Baseline
Clean-state baseline captured to C:\baseline-reference\
Files: processes.csv, services.csv, network.txt, users.csv,
admins.csv, scheduled-tasks.csv, startup.csv, installed-software.csv

## Forensic Artifact Locations
- Sysmon logs: Microsoft-Windows-Sysmon/Operational
- Security logs: C:\Windows\System32\winevt\Logs\Security.evtx
- Prefetch: C:\Windows\Prefetch\
- Amcache: C:\Windows\AppCompat\Programs\Amcache.hve
- Registry hives: C:\Windows\System32\config\
