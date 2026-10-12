# 2026-10-12 — Distinguish a virtual machine from its network

**Activity:** [Lab 01](../labs/01-virtualization-inventory.md) reflection, following the [skills calendar](../docs/infrastructure-skills-calendar.md).
**Status:** explanation attempted; correction supplied by mentor; understanding check pending.
**Evidence level:** Guided.

## Evidence and initial interpretation

The learner reviewed the [saved inventory](2026-10-09-virtualization-inventory.md): `win11-2` was `shut off`, and `default` was `active`. No new learning commands or output were supplied in this reflection; these remain earlier observations.

The learner described the virtual network as a virtual machine containing Windows, and reasoned that turning off the virtual environment would also turn off Windows. This exposed a specific gap: distinguishing the host, the guest VM, and its virtual network. The learner's statement that Windows can be turned on and off does not by itself establish understanding of those separate components.

## Mentor explanation

- The Debian host runs the virtualization software and the VM. Windows is the guest operating system inside `win11-2`.
- The virtual network provides connectivity for attached VMs; Windows does not run inside the network.
- A network can remain active with its VMs stopped, like a router remaining on while a computer is off.
- Stopping a virtual network does not necessarily stop an already-running VM; it can interrupt connectivity through that network. This is distinct from powering off the host, which cannot keep running its local VMs while powered off.
- An active network alone does not prove Windows internet access. Guest operation and its network path would need separate verification.

These are mentor-provided explanations, not learner-demonstrated conclusions or new fault-test results. No VM, service, or network was changed. No repair was needed or attempted.

## Next check and remaining uncertainty

Ask the learner to predict whether an already-running Windows VM must stop when its virtual network stops, and explain why. This is a hypothetical reasoning check only. Then revisit what an active network proves about internet access.

Do not advance to Explained until the learner demonstrates the distinction. Capacity checks and VM sizing remain pending; no new RAM or storage measurements have been supplied.

**AI assistance:** the assistant identified the conceptual gap, supplied the explanation and analogy, and prepared this documentation. The learner supplied the initial interpretation.
