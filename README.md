# Debian Linux Troubleshooting Lab

A practical troubleshooting portfolio documenting real problems encountered while configuring and administering a Debian GNU/Linux workstation.

The purpose of this repository is to show **how problems were investigated and solved**, not simply to list Linux commands.

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Desktop environment: KDE Plasma 6
- Hardware: HP EliteBook 840 G6
- CPU: Intel Core i5-8365U @ 1.60GHz
- Wi-Fi: Intel Wi-Fi 6 AX200
- External display: Toshiba via HDMI
- Virtualization: libvirt / QEMU / virt-manager
- Windows guest: Windows 11 (`win11-2`)
- Host libvirt connection: `qemu:///system`

## Troubleshooting Cases

1. [Network Connectivity and USB Tethering](troubleshooting/01-network-connectivity.md)
2. [APT Package and Repository Problems](troubleshooting/02-package-repositories.md)
3. [KDE Plasma Desktop Setup](troubleshooting/03-kde-plasma.md)
4. [Bluetooth and AirPods Troubleshooting](troubleshooting/04-bluetooth.md)
5. [Windows VM and libvirt Networking](troubleshooting/05-virtualization.md)
6. [HDMI Dual-Monitor Configuration](troubleshooting/06-dual-monitor-hdmi.md)
7. [Shutdown Investigation and Running VM](troubleshooting/07-shutdown-and-vm.md)
8. [Linux File Operations and `cat`](troubleshooting/08-file-operations-and-cat.md)

## Troubleshooting Method

Each case follows the same workflow:

1. Observe the symptom.
2. Gather evidence.
3. Form a hypothesis.
4. Run a targeted command.
5. Interpret the output.
6. Apply the smallest appropriate fix.
7. Test again.
8. Document the result.

This repository will continue to grow as new problems are encountered and solved on the Debian workstation.
