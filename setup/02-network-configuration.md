# 02 - Network Configuration

## Design Decision
Originally planned host-only networking. Switched to NAT Network
due to VirtualBox host network driver conflict with VirtualMachinePlatform
(required by WSL2) on the Windows 11 host.

## NAT Network Configuration
- Network name: dfir-lab
- IPv4 Prefix: 10.0.2.0/24 (VirtualBox default)
- DHCP: enabled
- Created via: File > Tools > Network Manager > NAT Networks

## VM Network Assignments
Both VMs use Adapter 1 attached to dfir-lab NAT Network.

| VM | MAC | IP |
|---|---|---|
| Parrot12 | 08:00:27:F3:22:3E | 10.0.2.15 |
| Windows-Target | 08:00:27:9D:7F:D3 | 10.0.2.3 |

## Connectivity Verification
Confirmed Windows-Target can ping Parrot12 (10.0.2.15).
Parrot cannot ping Windows-Target due to Windows Firewall
blocking inbound ICMP — expected behavior, not a network issue.

## Internet Access
Both VMs have internet access through the NAT gateway (10.0.2.1).
This is intentional for downloading tools and updates.
For malware analysis, a separate Internal Network adapter
will be used with no internet access.
