# 2026-10-12 — Check host capacity before building the server lab

**Goal:** identify available RAM and disk space before sizing a separate Debian server VM.
**Status:** host capacity and target filesystem checked; small server VM sizing selected; installer download and checksum check pending.
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

## Follow-up — verify stopped guest and compare memory

Following the shutdown instructions, the learner supplied a new Debian-host observation:

```bash
virsh -c qemu:///system list --all
```

```text
 Id   Name      State
--------------------------
 -    win11-2   shut off
```

The output confirms the stopped state. The learner did not separately describe the shutdown method used.

The learner then ran the requested read-only memory check on Debian:

```bash
free -h
```

```text
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       4.7Gi       1.9Gi       625Mi       1.8Gi       2.8Gi
Swap:          7.8Gi       4.1Gi       3.7Gi
```

**Mentor comparison:** available RAM increased from 1.5 to 2.8 GiB, approximately 1.3 GiB using the rounded displayed values. Used RAM fell from 6.1 to 4.7 GiB. These snapshots do not establish how much of the change is attributable solely to the VM, since other activity was not controlled. Swap occupancy increased from 2.6 to 4.1 GiB; the cause and current swap-in/out activity are unknown. Used swap need not immediately empty after RAM becomes available. No performance fault or complete resolution of memory pressure is claimed.

**Decision:** proceed with a modest starting allocation of 1 vCPU, 1 GiB RAM and a 20 GiB virtual disk for a Debian server without a desktop, keeping Windows stopped during lab use. The 2.8 GiB available snapshot supports this initial allocation with room for host/virtualization overhead, but is not a guarantee for every workload. No VM has yet been created.

**Next step — proposed, not executed:** run `virsh -c qemu:///system pool-list --all` to identify configured storage pools. If a pool named `default` is listed, inspect it with `virsh -c qemu:///system pool-dumpxml default` and identify its target path. Both checks are read-only. Otherwise, share the pool listing before selecting another pool. Confirm the target filesystem's capacity before creating a new disk; do not reuse the Windows disk.

The learner supplied both new outputs; the assistant supplied the comparison and sizing decision. Guided status is unchanged. This follow-up supersedes the earlier pending-shutdown status while preserving its historical observations.

## Follow-up — locate the VM storage pool

The learner ran these read-only commands in the Debian host terminal:

```bash
virsh -c qemu:///system pool-list --all
virsh -c qemu:///system pool-dumpxml default
```

The pool listing supplied was:

```text
 Name        State    Autostart
---------------------------------
 default     active   yes
 Downloads   active   yes
```

Selected lines from the supplied `default` pool XML are preserved below; the UUID and remaining XML are omitted:

```xml
<pool type='dir'>
  <name>default</name>
  <capacity unit='bytes'>241642119168</capacity>
  <allocation unit='bytes'>78170796032</allocation>
  <available unit='bytes'>163471323136</available>
```

The target path inside `<target>` was:

```xml
<path>/var/lib/libvirt/images</path>
```

**Mentor interpretation:** `default` is an active directory-backed storage pool. Its disk images live in `/var/lib/libvirt/images`. The storage pool named `default` is separate from the virtual network also named `default`; a shared name does not make them the same resource. The `Downloads` pool is listed but its target has not been inspected.

The reported available space exceeds the planned 20 GiB virtual disk size. It is a pool report, not a new `df` measurement of that exact target; its reported bytes differ from the earlier rounded `df` output. No cause for that difference is established here. Confirm the target filesystem before creating the disk. No repartitioning or reuse of the Windows disk is planned.

**Next checks — instructions only, not yet executed:**

```bash
df -hT /var/lib/libvirt/images
find "$HOME/Downloads" -maxdepth 1 -type f -iname '*debian*.iso'
```

Both run read-only on Debian without sudo. The first identifies the filesystem and space available at the selected storage target. The second looks only at files directly inside the usual Downloads directory for an existing Debian ISO; an empty result would not prove there is no installer elsewhere. Any existing ISO must be identified and verified before use. Do not assume the `Downloads` pool points to this home-directory path merely from its name.

The learner supplied the storage evidence; its interpretation and next checks are mentor-guided. No new storage volume, download, VM, or installation has been performed in this step.

## Follow-up — verify the target filesystem and prepare installation media

The learner ran `df -hT /var/lib/libvirt/images` on Debian and supplied:

```text
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2  ext4  226G   74G  141G  35% /
```

This confirms that the chosen VM storage directory uses the root ext4 filesystem and has 141G available in this snapshot. The planned new 20 GiB disk fits within the reported space. No repartitioning is needed for this plan.

The learner also supplied a Downloads search with no file paths returned. As pasted, the command was:

```bash
find "$HOME/Downloads" -maxdepth 1 -type f -iname '\*debian\*.iso'
```

The backslashes may be chat-formatting escapes; if entered literally inside the single quotes, they would prevent wildcard matching. Therefore this result is recorded only as no matching file reported, not proof that the computer has no ISO. The plan is to download a known official installer into a dedicated folder, without deleting existing files.

The assistant checked the [official Debian netinst page](https://www.debian.org/distrib/netinst). Its amd64 link pointed to `debian-13.7.0-amd64-netinst.iso` in the `current/amd64/iso-cd/` directory at this check. The web tool could not retrieve the binary or checksum file; no successful download or hash verification is claimed. [Debian's verification guide](https://www.debian.org/CD/verify) documents SHA512 checksum checks and separately explains signature authentication.

**Next milestone — instructions only:** download the amd64 netinst ISO and its `SHA512SUMS` file over HTTPS into `~/Downloads/debian-server-lab`, then compare the ISO with the published checksum. These commands have not yet been reported executed:

```bash
mkdir -p "$HOME/Downloads/debian-server-lab" && cd "$HOME/Downloads/debian-server-lab"
wget --no-clobber https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-13.7.0-amd64-netinst.iso
wget --no-clobber https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/SHA512SUMS
sha512sum --ignore-missing -c SHA512SUMS
```

Run on the Debian host without sudo; stop if folder creation/change or a download fails. This creates a directory and downloads files but installs no packages or OS. `--no-clobber` preserves existing files. Success requires the expected ISO filename with an `OK` checksum result; errors or a mismatch must be reviewed before use. This is an integrity comparison against the HTTPS-published checksum, not a completed OpenPGP signature check. No ISO download, checksum result, or new server VM is yet claimed.
