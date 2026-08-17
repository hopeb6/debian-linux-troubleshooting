# 07 — Investigating Debian Shutdown and the Running VM

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Desktop: KDE Plasma 6
- Virtualization: QEMU/KVM + libvirt
- VM: `win11-2`

## Problem

The Debian machine was taking approximately five minutes to shut down.

## Investigation

### Command

```bash
journalctl -b -1 -o short-monotonic | tail -200
```

### Why

`journalctl` reads system logs.

- `-b -1` selects the previous boot, which is useful after restarting when investigating what happened before the current boot.
- `-o short-monotonic` shows monotonic timestamps, making the sequence easier to compare.
- `tail -200` limits the output to the last 200 log lines.

## Evidence

The logs showed a normal KDE logout and shutdown sequence.

Examples included:

```text
Activating service name='org.kde.Shutdown'
```

followed by:

```text
Stopped plasma-workspace.target
Stopped plasma-plasmashell.service
Stopped plasma-kwin_wayland.service
Reached target shutdown.target
Reached target exit.target
```

There were also warnings and application errors involving KDE/Qt, PipeWire, Chrome, PAM and Wayland. These did not by themselves prove that the shutdown process was failing.

## Important Observation

The log also showed virt-manager and the Windows VM environment consuming significant resources while they were running.

The practical test was to shut down Windows first, close virt-manager, and then shut down Debian.

## Solution

The Windows guest was shut down cleanly **before** shutting down the Debian host.

The normal shutdown order is therefore:

1. Shut down Windows from inside the VM.
2. Confirm the VM has stopped.
3. Close virt-manager.
4. Shut down Debian.

## Result

The long shutdown behaviour was resolved when the Windows VM was shut down before the Debian host.

## Lesson Learned

Host and guest operating systems have separate lifecycles.

A virtual machine should be shut down cleanly before powering off the host rather than relying on the host to terminate the guest during shutdown.

This troubleshooting exercise also reinforced the importance of reading logs in context rather than treating every warning as the root cause.

## Skills Demonstrated

- `journalctl`
- systemd shutdown analysis
- KDE session management
- Log interpretation
- Virtualization administration
- Host/guest lifecycle management
