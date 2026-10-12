# Learning progress

## Current milestone

Prepare the separate Debian server lab using the [2026-10-12 capacity check](journal/2026-10-12-host-capacity.md). The learner correctly identified 1.5 GiB available RAM and 141G available filesystem space after command guidance. Next, recheck RAM after closing unused applications, confirm the VM storage location, and choose safe VM resources.

[Lab 01](labs/01-virtualization-inventory.md) remains Guided: its [outputs](journal/2026-10-09-virtualization-inventory.md) are recorded, and the [reflection](journal/2026-10-12-inventory-reflection.md) identified confusion between a VM and its virtual network. Revisit their roles during practical setup rather than continuing a separate verbal quiz.

The learner reports that the earlier investigations used AI guidance and that recalling commands is difficult. Current emphasis: choosing a check, interpreting evidence, and repeating a task with decreasing help. This is an assessment baseline, not a proficiency certification.

## Evidence levels

- **Guided:** completed or reported with assistance; may still require substantial help.
- **Explained:** learner has explained the evidence and reasoning in their own words.
- **Repeated with reference:** learner completed a new attempt using notes or official documentation without step-by-step prompting.
- **Transferred:** learner diagnosed a related but unfamiliar variation and verified the outcome.

Looking up syntax is permitted at every level. A published note alone does not advance the level.

| Topic | Existing record | Current evidence | Next proof |
| --- | --- | --- | --- |
| Interfaces, connectivity and DNS | [01](troubleshooting/01-network-connectivity.md) | Guided; original diagnostic output incomplete | Explain a fresh interface/route/name-resolution observation |
| Package repositories | [02](troubleshooting/02-package-repositories.md) | Guided; reported repository errors | Interpret a real package-index error without assuming the final summary proves success |
| Desktop setup | [03](troubleshooting/03-kde-plasma.md) | Guided | Explain the dependency chain; no reinstall required |
| Bluetooth | [04](troubleshooting/04-bluetooth.md) | Guided; exact repair sequence incomplete | Explain one useful service/log observation |
| Virtualization and network context | [05](troubleshooting/05-virtualization.md), [Lab 01 attempt](journal/2026-10-09-virtualization-inventory.md), [reflection](journal/2026-10-12-inventory-reflection.md) | Guided; outputs supplied; initial explanation confused VM and virtual network; mentor correction given | Distinguish host, guest VM and virtual network; explain why network state alone does not prove guest internet access |
| Host memory and storage | [Capacity check](journal/2026-10-12-host-capacity.md) | Guided execution; learner correctly identified available RAM and disk fields after column guidance | Compare a fresh memory snapshot and help choose VM resources; independent capacity diagnosis unassessed |
| Display setup | [06](troubleshooting/06-dual-monitor-hdmi.md) | Guided | Explain extended versus mirrored layout |
| Shutdown and VM lifecycle | [07](troubleshooting/07-shutdown-and-vm.md) | Guided; improvement reported, precise delay mechanism unproven | Separate observed timing from a root-cause hypothesis |
| Paths and file operations | [08](troubleshooting/08-file-operations-and-cat.md) | Guided | Explain paths and overwrite behaviour in a disposable example |
| SSH and GitHub | [09](troubleshooting/09-ssh-setup.md) | Existing note reports successful authentication/clone; repeatability not assessed | Review the draft's duplicated text and technical claims, then explain a new authentication check |

## Upcoming activity

- [x] Supply and record both Lab 01 inventory outputs from the learner's Debian host; no error supplied.
- [ ] Explain VM state and virtual-network state in the learner's own words.
- [ ] Add the learner's explanation and publish the completed lab assessment; the recorded attempt remains guided.
- [ ] Repeat the observation later with fewer hints.
- [x] Capture initial available RAM/disk and review the learner's reading of the output.
- [ ] Recheck available RAM after closing unused applications; confirm VM storage location before sizing the disposable server lab.

## Documentation review queue

- Case 01: an inactive `systemd-networkd` is not by itself proof of broken networking; establish which manager owns the interface before recommending a restart.
- Case 05: the observed sudo/non-sudo connection difference is setup-specific. Select the intended connection explicitly rather than assuming a universal default.
- Case 07: distinguish the reported improvement after stopping the guest from an unverified explanation of why shutdown was delayed.
- Case 09: duplicated sections and unclosed fences need a separate cleanup. Correct broad claims that all cloud systems use SSH, that Ed25519 is universally the strongest option, or that private-key authentication is immune to compromise. Preserve the reported result as historical evidence.

Latest journal entry: [2026-10-12 host capacity](journal/2026-10-12-host-capacity.md). The [inventory reflection](journal/2026-10-12-inventory-reflection.md), [2026-10-09 inventory](journal/2026-10-09-virtualization-inventory.md), and [initial learning baseline](journal/2026-10-08-learning-baseline.md) preserve earlier observations and assessment.
