# 2026-10-09 — Read-only virtualization inventory

**Lab:** [Lab 01](../labs/01-virtualization-inventory.md)
**Status:** both command outputs supplied; learner explanation still pending.
**Assistance:** guided commands and mentor interpretation; no independent mastery claimed.

## Goal and success criteria

Observe VMs and virtual networks through the explicit system libvirt connection, then explain what the results establish and leave unknown. Observation and an accurate learner explanation are required to complete the lab. No VM or network changes are part of this exercise.

## Learner actions and evidence

The learner supplied these outputs from commands run on the Debian host, outside the Windows guest. The VM output was carried forward from the previous mentoring chat; its exact execution date/time was not supplied. The network output was supplied in this session. These are separate observations, not a simultaneous health check.

VM inventory — list all VMs known to the system connection, including stopped VMs:

```bash
virsh -c qemu:///system list --all
```

```text
 Id   Name      State
--------------------------
 -    win11-2   shut off
```

Network inventory — list active and inactive libvirt networks in the same connection:

```bash
virsh -c qemu:///system net-list --all
```

```text
 Name      State    Autostart   Persistent
--------------------------------------------
 default   active   yes         yes
```

No permission or connection error was included with either learner-supplied result.

## Mentor interpretation

- `win11-2` is listed and was stopped (`shut off`). The dash means it had no active runtime ID. This explanation came from the previous mentor.
- `default` was active when checked. `Autostart: yes` means it is configured to start automatically when the relevant libvirt daemon starts; it is a setting, separate from the current state.
- `Persistent: yes` means the network has a saved definition that remains when the network is stopped. It does not mean the network must always be active.
- A virtual network can be active while a VM is stopped. These outputs do not establish the VM's current network attachment, guest IP address, DNS operation, or internet connectivity.

## Verification and limits

Both supplied commands explicitly select `qemu:///system`. Their outputs establish the listed resource states at their respective observation times. No guest connectivity test, reboot/autostart test, or repair was performed as part of this lab. There is no demonstrated fault and no fix to apply from this evidence.

Historical results in [case 05](../troubleshooting/05-virtualization.md) remain historical; they were not substituted for this attempt.

## Assistance and next step

The learner ran the learning commands and supplied the evidence. The assistant reviewed repository instructions and history, interpreted the evidence, and prepared the documentation. The assistant did not run the inventory commands on the learner's behalf.

Evidence remains **Guided**. A command-purpose prediction and the learner's own interpretation have not yet been supplied; repetition without step-by-step prompting and independent application remain unassessed.

Next: in the learner's own words, explain how `default` can be active while `win11-2` is stopped and whether these observations prove Windows internet access. No additional command is needed for that reflection.

## Assistant publication checks

From the canonical repository, the assistant ran `git ls-remote origin refs/heads/main`. It failed with `Bad owner or permissions on /etc/ssh/ssh_config.d/20-systemd-ssh-proxy.conf`. A command-scoped retry using `git -c core.sshCommand='ssh -F /dev/null' ls-remote origin refs/heads/main` bypassed SSH configuration files but initially failed with `Could not resolve hostname github.com: Temporary failure in name resolution` inside the sandbox.

The same retry outside the network sandbox succeeded and returned `816120d33707a74ae2a860dfac1bfc1a3845a47b` for remote `main`, matching the local starting commit. No SSH configuration file was changed. The underlying configuration error was not investigated or repaired; these were assistant publishing checks, not learner troubleshooting evidence.
