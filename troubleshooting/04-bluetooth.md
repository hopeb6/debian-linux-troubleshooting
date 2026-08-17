# 04 — Bluetooth and AirPods Troubleshooting

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Desktop: KDE Plasma 6
- Bluetooth stack: BlueZ
- Bluetooth hardware: Intel AX200 platform

## Problem

Bluetooth devices, including AirPods, needed to be detected and connected on Debian.

## Investigation

### Command

```bash
lsusb
```

### Why

`lsusb` identifies USB hardware. It was used to confirm that the Bluetooth hardware was visible to the operating system.

### Command

```bash
bluetoothctl
```

### Why

`bluetoothctl` is the command-line interface for the BlueZ Bluetooth stack. It allows Bluetooth devices to be discovered, paired, trusted and connected.

### Command

```bash
journalctl -u bluetooth
```

### Why

This displays logs for the Bluetooth service and helps identify service-level or permission problems.

## Solution

The Bluetooth controller and service were investigated with the BlueZ tooling. The AirPods were then successfully connected.

## Result

Bluetooth was operational and the AirPods could connect to the Debian machine.

## Lesson Learned

Hardware troubleshooting should begin by establishing that the operating system can actually see the hardware before changing higher-level configuration.

A useful chain is:

```text
Hardware → kernel/USB → BlueZ → bluetoothctl → desktop integration → audio
```

## Skills Demonstrated

- Bluetooth administration
- BlueZ
- `bluetoothctl`
- `journalctl`
- Hardware identification
- Linux device troubleshooting
