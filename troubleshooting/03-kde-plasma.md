# 03 — KDE Plasma Desktop Setup

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Hardware: HP EliteBook 840 G6
- Initial installation: minimal Debian installation
- Target desktop: KDE Plasma 6

## Problem

Debian was initially installed without a graphical desktop environment. The system therefore started primarily as a terminal-based installation.

## Symptoms

The normal KDE graphical desktop was unavailable.

### Command

```bash
ls /usr/share/xsessions
```

### Result

The directory did not exist, which was consistent with the expected graphical desktop session files not being installed.

## Investigation

### Command

```bash
sudo apt install task-kde-desktop
```

### Why

`task-kde-desktop` is a Debian task package used to install KDE Plasma and associated desktop components.

The installation initially could not proceed because APT itself was not correctly accessing the Debian repositories. That problem was investigated separately in [02 — APT Package and Repository Problems](02-package-repositories.md).

## Solution

The package-management and network problems were resolved first.

KDE Plasma was then installed and configured as the graphical desktop environment.

## Result

The Debian machine became a functional KDE Plasma workstation and could run graphical applications such as:

- Konsole
- Dolphin
- KDE Discover
- virt-manager
- Bluetooth tools
- HDMI display configuration

## Lesson Learned

Linux system configuration often has dependencies:

```text
Network → APT → Desktop packages → KDE Plasma → Applications
```

Trying to troubleshoot the graphical desktop before fixing the underlying package-management problem would not have solved the root cause.

## Skills Demonstrated

- Debian installation
- APT package management
- KDE Plasma administration
- Linux desktop configuration
- Troubleshooting installation dependencies
