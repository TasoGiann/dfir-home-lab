# dfir-home-lab

Documentation of my segmented DFIR home lab: network design, VM specifications,
setup steps, baseline snapshots, and lessons learned.

## Lab Environment

- **Host:** MSI Cyborg 15 (16 GB RAM, Windows 11)
- **Hypervisor:** Oracle VirtualBox
- **Network:** dfir-lab NAT Network (10.0.2.0/24)
- **VMs:**
  - `Parrot12` — Parrot OS 6.19.6, analyst workstation (10.0.2.15)
  - `Windows-Target` — Windows 11 Enterprise Eval, investigation target

## Network Design

Both VMs connect through a VirtualBox NAT Network called dfir-lab.
This provides VM-to-VM connectivity while sharing internet access
through the host. Chosen over host-only networking due to a VirtualBox
host network driver conflict with VirtualMachinePlatform on the host OS.

## Structure

- `diagrams/` — network topology diagrams
- `vms/` — one markdown file per VM
- `setup/` — numbered setup documentation
- `baselines/` — clean-state captures
- `docs/` — general documentation
- `lessons-learned.md` — what broke and what I learned

## Status

Lab operational. Windows-Target installation in progress.
