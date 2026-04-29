# Parrot12 (Analyst VM)

## Specifications
- OS: Parrot OS 6.19.6 (Debian-based, 64-bit)
- RAM: 3072 MB
- CPUs: 4
- Disk: 50 GB
- Hypervisor: VirtualBox
- Network: dfir-lab NAT Network (10.0.2.0/24)
- IP: 10.0.2.15 (DHCP)
- Local user: tasos (sudo)

## Purpose
Primary analyst workstation. Used for:
- Running investigation tools against the Windows target
- Scripting and automation
- Log analysis and parsing
- Network traffic capture and analysis
- Documentation and reporting

## Pre-installed Tools (Parrot Security Edition)
- Wireshark
- Nmap
- Metasploit
- Docker
- Python 3
- Git

## Configuration Changes from Default
- sudo password set via pkexec
- dfir-home-lab git repository initialized
- Git identity configured

## Network Connectivity
- Can reach Windows-Target at 10.0.2.3
- Confirmed via ping from Windows-Target
- Note: Windows Firewall blocks ICMP from Parrot (expected)
