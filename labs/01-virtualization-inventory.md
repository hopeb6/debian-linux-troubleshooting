# Lab 01 — Observe the current virtualization state

**Status:** both outputs recorded in the [2026-10-09 journal](../journal/2026-10-09-virtualization-inventory.md); learner interpretation pending.
**Environment:** learner's Debian host with existing libvirt/virt-manager installation.
**Scope:** observation only. Do not stop/start a VM or change the working virtual network for this exercise.

## Why this matters

An empty list may reflect the wrong management connection, not missing resources. Learn to select an explicit connection and interpret VM and network states before proposing a change.

## Checks

Before each command, say what question it should answer. Notes are allowed.

```bash
virsh -c qemu:///system list --all
virsh -c qemu:///system net-list --all
```

The first lists VMs in that connection, including stopped ones. The second lists its virtual networks, including inactive ones. `-c` chooses the connection explicitly. See the [question-based reference](../reference/command-notebook.md).

If a command reports a permission, connection or missing-command error, save the relevant message and ask for interpretation. An error is a valid result; no configuration change is required to finish documenting the attempt.

## Explain the evidence

1. Is the expected Windows VM listed? What is its state?
2. Is a network named `default` listed? What is its state?
3. Does an active virtual network alone prove that Windows can reach the internet? Explain the limit of this observation.

The old screenshots or example outputs in case 05 are historical; do not use them as the result of this attempt.

## Success and record

Success is executing the observations and correctly explaining what the output does or does not show, or accurately documenting a blocking error. Working from a reference is expected.

Add `journal/YYYY-MM-DD-virtualization-inventory.md` with command purpose, actual output excerpt, interpretation, assistance used and the next check. Update the virtualization row in [learning progress](../learning-progress.md) only when there is evidence for a new level. Review and publish the entry using [the workflow](../docs/workflow.md).

No intentional fault is part of this lab. Later failure/recovery exercises will use a disposable environment.
