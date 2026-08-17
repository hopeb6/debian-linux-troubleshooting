# 02 — APT Package and Repository Problems

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Package manager: APT
- Initial goal: install/configure KDE Plasma

## Problem

APT was not behaving normally while attempting to install desktop packages.

## Symptoms

Commands such as:

```bash
sudo apt install task-kde-desktop
```

returned:

```text
Unable to locate package task-kde-desktop
```

APT also reported repository and DNS errors involving Debian mirrors.

## Investigation

### Command

```bash
sudo apt update
```

### Why

`apt update` refreshes the local package index from configured repositories. It is the first check when APT cannot find a package.

### Command

```bash
cat /etc/apt/sources.list
```

### Why

This was used to inspect the repository configuration directly.

### Observed problems

The repository configuration contained malformed/duplicate entries at one stage, and APT reported failures resolving Debian repository domains.

Examples included:

```text
Temporary failure resolving 'deb.debian.org'
Temporary failure resolving 'security.debian.org'
```

## Solution

The APT repository configuration and the underlying network/DNS problems were investigated and corrected so that Debian could successfully access its configured package repositories.

Once APT was functioning correctly, package installation could proceed.

## Result

APT became usable for installing the desktop environment and other required packages.

## Important Observation

At one stage `apt update` also displayed:

```text
All packages are up to date.
```

even though the update output contained repository errors.

This showed that the final summary line must not be read in isolation. The complete output needs to be checked for `Err:`, `Ign:`, DNS failures, duplicate entries, and malformed repository lines.

## Lesson Learned

When `apt install` says a package cannot be located, check the package repositories before assuming the package does not exist.

A practical troubleshooting sequence is:

1. Check network connectivity.
2. Check DNS.
3. Inspect repository configuration.
4. Run `sudo apt update`.
5. Read the complete output.
6. Retry the package installation.

## Skills Demonstrated

- APT
- Debian repositories
- DNS troubleshooting
- Package-manager troubleshooting
- Reading system configuration
