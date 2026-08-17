# 05 — Windows VM and libvirt Networking

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Virtualization: QEMU/KVM + libvirt
- Management tool: virt-manager
- Guest OS: Windows 11
- VM name: `win11-2`
- Correct libvirt connection: `qemu:///system`

## Problem

The Windows virtual machine failed to start from virt-manager.

## Error

```text
Error starting domain: Requested operation is not valid:
network 'default' is not active
```

## Investigation

The error indicated that the VM depended on libvirt's `default` virtual network, but that network was not active at the time.

### Important discovery: libvirt connections

Running:

```bash
virsh uri
```

returned:

```text
qemu:///session
```

Running:

```bash
sudo virsh uri
```

returned:

```text
qemu:///system
```

This explained why earlier `virsh` commands appeared to show no VM or network. The non-sudo command was checking the user-level libvirt session, while the actual Windows VM managed by virt-manager was under the system-level connection.

### Correct connection

The actual system-level resources were verified with:

```bash
sudo virsh list --all
```

Result:

```text
Id   Name      State
-------------------------
1    win11-2   running
```

The system-level libvirt networks were verified with:

```bash
sudo virsh net-list --all
```

Result:

```text
Name      State    Autostart   Persistent
--------------------------------------------
default   active   yes         yes
```

## Fix / Resolution

The `default` virtual network was ultimately brought into a working state, allowing the Windows VM to start.

The exact command used at the time of the original fix was not captured in the troubleshooting notes, so this portfolio does not claim a specific command that was not verified.

The current configuration is:

```text
Libvirt connection: qemu:///system
VM:                  win11-2
Network:             default
Network state:       active
Autostart:           yes
Persistent:          yes
```

## Result

The Windows VM runs successfully under virt-manager.

## Lesson Learned

`virsh` can connect to different libvirt instances. A VM or network can appear to be missing simply because the command is looking at the wrong connection.

For system-level libvirt resources:

```bash
sudo virsh ...
```

uses:

```text
qemu:///system
```

while:

```bash
virsh ...
```

uses the user's session:

```text
qemu:///session
```

This was a practical example of troubleshooting a service dependency and validating the correct management context before changing configuration.

## Skills Demonstrated

- QEMU/KVM
- libvirt
- virt-manager
- `virsh`
- Virtual networking
- Linux virtualization troubleshooting
- Service/resource dependency analysis
