# 2026-10-12 — Check host capacity before building the server lab

**Goal:** identify available RAM and disk space before sizing a separate Debian server VM.
**Status:** initial capacity and follow-up process measurements received; Windows now observed running; shutdown comparison and VM storage location pending.
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

## Initial next step — proposed, not reported performed

Save work, close a few unused desktop applications or browser tabs normally, then rerun `free -h` on the Debian host and compare the available value. Do not stop host services, kill unfamiliar processes, or clear swap for this exercise. No application closure or improved measurement has been reported yet.

After the updated measurement, confirm the VM storage location and choose a conservative configuration. No new VM, installation, or resource allocation has been performed in this attempt.

## Learning continuity

The [earlier VM/network reflection](2026-10-12-inventory-reflection.md) remains Guided. The learner requested practical work rather than further conceptual questioning; revisit that distinction during setup. It has not been marked independently explained.

The assistant reviewed the evidence and prepared these notes; the assistant did not run the learner's capacity commands. The successful part of this milestone is accurate reading of the supplied available-memory and storage fields, not completion of the server build.

## Follow-up — identify the main memory consumer

After discussing removal of Windows or repartitioning, the mentor proposed checking current VM state and the largest processes before making changes. The learner ran these read-only commands on the Debian host:

```bash
virsh -c qemu:///system list --all
```

```text
 Id   Name      State
-------------------------
 1    win11-2   running
```

```bash
ps -eo pid,comm,rss --sort=-rss | head -n 11
```

```text
    PID COMMAND           RSS
  16336 qemu-system-x86 3594196
   6949 chrome          551608
   4295 chrome          486468
   2974 ChatGPT         280916
   1536 plasmashell     227728
   7384 chrome          158284
   1936 chrome          158068
   4274 chrome          149604
   4030 chrome          146752
   1933 ChatGPT         146012
```

**Mentor interpretation:** Windows is running in this new observation. The older `shut off` result remains valid for its earlier observation time and must not be treated as current. QEMU is the largest listed process: 3,594,196 KiB RSS is approximately 3.43 GiB of resident memory. This strongly suggests the Windows VM is the main memory consumer in this snapshot, although these commands do not explicitly map PID 16336 to the named domain. RSS is not the VM's configured RAM allocation, and shared pages mean process RSS values should not simply be summed as unique system memory.

**Updated decision:** plan to run one guest at a time. Removing a stopped Windows VM would reclaim storage, not its former running memory. Repartitioning does not add RAM; current filesystem space is adequate for a small lab disk if the chosen VM storage location uses that filesystem. No deletion or partition change is needed on this evidence.

The proposed server configuration is 1 vCPU, 1 GiB RAM, and a 20 GiB virtual disk, without a graphical desktop. This is a starting configuration for small SSH/Nginx and administration exercises, subject to post-shutdown capacity and storage-location checks. [Debian's installation guidance](https://www.debian.org/releases/trixie/amd64/ch03s04.en.html) recommends 1 GB RAM for a basic installation without a desktop and notes that server requirements depend on workload. This proposed VM has not been created.

**Next step, instructions only:** when finished using Windows, save work inside the guest and use Windows' normal Shut down action. Then run `virsh -c qemu:///system list --all` and `free -h` on Debian. Success means a confirmed `shut off` state and a new available-memory measurement for comparison; the amount reclaimed is not yet known. Closing the VM viewer alone is not verification of shutdown. This targeted comparison supersedes the earlier generic suggestion to close desktop applications.

No shutdown, memory improvement, or new installation has yet been reported. The assistant did not operate the guest or run these learning checks. Interpretation remains mentor-guided.
