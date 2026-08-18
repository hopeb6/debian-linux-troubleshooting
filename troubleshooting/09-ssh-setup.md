# 09 — SSH Key Setup and GitHub Authentication

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Hardware: HP EliteBook 840 G6
- Shell: Bash
- Service: GitHub (github.com/hopeb6)

## Problem / Goal

To connect the Debian machine to GitHub securely using SSH key 
authentication instead of a username and password.

This is foundational for DevOps work because every cloud server, 
Azure VM, and remote system is accessed through SSH.

## Commands Used

### Command

```bash
ssh-keygen -t ed25519 -C "hopebirungi218@gmail.com"
```

### Why

Generates an SSH key pair — a private key that stays on the local 
machine and a public key that is copied to remote servers or services. 
Ed25519 is currently the strongest available algorithm for SSH keys.

### Command

```bash
ls ~/.ssh/
```

### Why

Confirms the two key files were created successfully:
- `id_ed25519` — private key, never shared
- `id_ed25519.pub` — public key, copied to GitHub

### Command

```bash
cat ~/.ssh/id_ed25519.pub
```

### Why

Reads and prints the public key to the terminal so it can be copied 
and added to GitHub under Settings → SSH and GPG keys.

### Command

```bash
ssh -T git@github.com
`# 09 — SSH Key Setup and GitHub Authentication

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Hardware: HP EliteBook 840 G6
- Shell: Bash
- Service: GitHub (github.com/hopeb6)

## Problem / Goal

To connect the Debian machine to GitHub securely using SSH key 
authentication instead of a username and password.

This is foundational for DevOps work because every cloud server, 
Azure VM, and remote system is accessed through SSH.

## Commands Used

### Command

```bash
ssh-keygen -t ed25519 -C "hopebirungi218@gmail.com"
```

### Why

Generates an SSH key pair — a private key that stays on the local 
machine and a public key that is copied to remote servers or services. 
Ed25519 is currently the strongest available algorithm for SSH keys.

### Command

```bash
ls ~/.ssh/
```

### Why

Confirms the two key files were created successfully:
- `id_ed25519` — private key, never shared
- `id_ed25519.pub` — public key, copied to GitHub

### Command

```bash
cat ~/.ssh/id_ed25519.pub
```

### Why

Reads and prints the public key to the terminal so it can be copied 
and added to GitHub under Settings → SSH and GPG keys.

### Command

```bash
ssh -T git@github.com
# 09 — SSH Key Setup and GitHub Authentication

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Hardware: HP EliteBook 840 G6
- Shell: Bash
- Service: GitHub (github.com/hopeb6)

## Problem / Goal

To connect the Debian machine to GitHub securely using SSH key 
authentication instead of a username and password.

This is foundational for DevOps work because every cloud server, 
Azure VM, and remote system is accessed through SSH.

## Commands Used

### Command

```bash
ssh-keygen -t ed25519 -C "hopebirungi218@gmail.com"
```

### Why

Generates an SSH key pair — a private key that stays on the local 
machine and a public key that is copied to remote servers or services. 
Ed25519 is currently the strongest available algorithm for SSH keys.

### Command

```bash
ls ~/.ssh/
```

### Why

Confirms the two key files were created successfully:
- `id_ed25519` — private key, never shared
- `id_ed25519.pub` — public key, copied to GitHub

### Command

```bash
cat ~/.ssh/id_ed25519.pub
```

### Why

Reads and prints the public key to the terminal so it can be copied 
and added to GitHub under Settings → SSH and GPG keys.

### Command

```bash
ssh -T git@github.com
```
# 09 — SSH Key Setup and GitHub Authentication

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Hardware: HP EliteBook 840 G6
- Shell: Bash
- Service: GitHub (github.com/hopeb6)

## Problem / Goal

To connect the Debian machine to GitHub securely using SSH key 
authentication instead of a username and password.

This is foundational for DevOps work because every cloud server, 
Azure VM, and remote system is accessed through SSH.

## Commands Used

### Command

```bash
ssh-keygen -t ed25519 -C "hopebirungi218@gmail.com"
```
## Why

Generates an SSH key pair — a private key that stays on the local 
machine and a public key that is copied to remote servers or services. 
Ed25519 is currently the strongest available algorithm for SSH keys.

### Command

```bash
ls ~/.ssh/
```

### Why

Confirms the two key files were created successfully:
- `id_ed25519` — private key, never shared
- `id_ed25519.pub` — public key, copied to GitHub

### Command

```bash
cat ~/.ssh/id_ed25519.pub
```
### Why

Reads and prints the public key to the terminal so it can be copied 
and added to GitHub under Settings → SSH and GPG keys.

### Command

```bash
ssh -T git@github.com
```

### Why

Tests whether GitHub recognizes the SSH key. The `-T` flag means 
test the connection without opening a full terminal session.

### Command

```bash
git config --global user.name "Your Name"
git config --global user.email "hopebirungi218@gmail.com"
```
### Why

Configures Git identity so every commit is stamped with the correct 
name and email. `--global` applies this to all repositories on the 
machine.

### Command

```bash
git clone git@github.com:hopeb6/debian-linux-troubleshooting.git
```

### Why

Downloads the existing GitHub repository onto the local Debian machine 
and connects it to GitHub via SSH. From this point, changes can be 
pushed from the terminal without using a browser.

## Result

GitHub responded with:
Hi hopeb6! You've successfully authenticated, but GitHub does not
provide shell access.
The repository was cloned successfully and git status confirmed the 
local copy was in sync with GitHub.

## Lesson Learned

SSH key authentication is more secure than passwords because the 
private key cannot be guessed or brute forced. An attacker without 
the private key file cannot gain access regardless of how many 
attempts they make.

The public key is like a padlock placed on a door. The private key 
is the physical key that opens it. Only someone with the correct key 
can open the padlock.

## Skills Demonstrated

- SSH key generation
- Ed25519 encryption
- GitHub SSH authentication
- Git configuration
- Repository cloning
- Terminal-based GitHub workflow
