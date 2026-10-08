# Command notebook

Use this as an open-book reference. Remember the question each command answers;
you can look up its spelling. These entries explain commands and possible
results. They are **not evidence that a command was run or a skill mastered**.
Record actual practice, dates, and results separately.

## Which virtual machines exist on my system libvirt connection?

```bash
virsh -c qemu:///system list --all
```

- **Where:** a terminal on the Debian host, not inside the Windows guest.
- **Purpose:** list both running and stopped VMs known to the system connection.
- **Read the command:** `-c qemu:///system` selects the connection; `list`
  lists VMs; `--all` includes stopped VMs.
- **Safety:** read-only; does not start, stop, or change a VM. Access may require
  authorization depending on the host's configuration.
- **Interpretation:** `running` means libvirt reports the VM running; `shut off`
  means it is stopped. An empty list means no VMs are listed in this connection,
  not that all VMs on the computer have been deleted.
- **Limit:** a running state does not establish that Windows or an application
  inside the guest is healthy.

## Is the virtual network available in that connection?

```bash
virsh -c qemu:///system net-list --all
```

- **Where:** a terminal on the Debian host.
- **Purpose:** list the system connection's active and inactive libvirt networks.
- **Read the command:** `net-list` lists virtual networks; `--all` includes
  inactive networks.
- **Safety:** read-only; does not activate or modify a network.
- **Interpretation:** `active` means the network is started. `Autostart: yes`
  means it is configured to start automatically; it does not by itself mean the
  network is active now. `Persistent: yes` means its definition persists beyond
  the current active instance.
- **Limit:** an active network alone does not prove that a guest has an IP
  address, working DNS, or internet access.

## What should I do with an unexpected result?

Write down the exact command, connection, and redacted output before proposing
a change. A permission or connection error is not the same as an empty list.
Ask what the result proves and what it leaves unknown.

The [original virtualization case](../troubleshooting/05-virtualization.md)
observed different results from the user session and system connection. Those
were observations from that setup: using `sudo` is not a universal guarantee of
which connection a command selects. The commands above make the connection
explicit. The case's earlier results do not establish the host's current state.

## Add the next command

For each new entry, record the question, exact command, where to run it, whether
it changes anything, how to interpret a result, and one thing it cannot prove.
