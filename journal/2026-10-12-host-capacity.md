# 2026-10-12 — Check host capacity before building the server lab

**Goal:** identify available RAM and disk space before sizing a separate Debian server VM.
**Status:** initial measurements received; VM sizing and storage location pending.
**Assistance:** mentor supplied commands and column guidance; learner ran them and correctly identified the available values.

## Learner commands and evidence

Run in the Debian host terminal, outside the Windows guest. Both commands are read-only and require no sudo. Shell prompt omitted from the evidence excerpt.

```bash
free -h
```

```text
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       6.1Gi       438Mi       720Mi       2.0Gi       1.5Gi
Swap:          7.8Gi       2.6Gi       5.2Gi
```

```bash
df -hT / /home
```

```text
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2  ext4  226G   73G  141G  35% /
/dev/nvme0n1p2  ext4  226G   73G  141G  35% /
```

The learner identified **1.5Gi available RAM** and **141G available disk space**. Both match the supplied output. This demonstrates correct identification of those two fields after guidance; independent command selection and broader resource diagnosis remain unassessed.

## Mentor interpretation and decision

- Total RAM is 7.6 GiB. The 1.5 GiB available estimate is more useful for initial capacity planning than the 438 MiB completely free value, because some memory can be reclaimed.
- Swap has 2.6 GiB in use. Swap is disk-backed memory support, not additional physical RAM. Its occupancy alone does not show current swap activity or prove a performance problem.
- `/` and `/home` resolve to the same ext4 filesystem on `/dev/nvme0n1p2`; the repeated 141G is one shared amount, not two allocations. GNU `df -h` uses powers of 1024, so this represents approximately 141 GiB.
- RAM is the immediate constraint. Avoid assigning a 2 GiB guest on the assumption that the current 1.5 GiB available snapshot provides comfortable headroom. Final VM sizing is not yet decided.
- Storage appears sufficient for a small lab disk if it will reside on this filesystem, but the actual VM storage location must be confirmed first.

## Next step — proposed, not yet performed

Save work, close a few unused desktop applications or browser tabs normally, then rerun `free -h` on the Debian host and compare the available value. Do not stop host services, kill unfamiliar processes, or clear swap for this exercise. No application closure or improved measurement has been reported yet.

After the updated measurement, confirm the VM storage location and choose a conservative configuration. No new VM, installation, or resource allocation has been performed in this attempt.

## Learning continuity

The [earlier VM/network reflection](2026-10-12-inventory-reflection.md) remains Guided. The learner requested practical work rather than further conceptual questioning; revisit that distinction during setup. It has not been marked independently explained.

The assistant reviewed the evidence and prepared these notes; the assistant did not run the learner's capacity commands. The successful part of this milestone is accurate reading of the supplied available-memory and storage fields, not completion of the server build.
