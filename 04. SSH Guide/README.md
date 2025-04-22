# SSH Guide

## Installation

### Using apt package manager
```bash
sudo apt install openssh-clients openssh-server
```

### Using yum package manager
```bash
sudo yum install openssh-clients openssh-server
```

### Using zypper package manager
```bash
sudo zypper install openssh
```

## Generate SSH Key Pair
```bash
ssh-keygen
```

- It will ask where to save the key (default is ~/.ssh/id_rsa).
- It will prompt for a passphrase (you can leave it empty or enter one for extra security).
- Confirm the passphrase.

### This creates two files:
- Private key: `~/.ssh/id_rsa` (keep this secure and private)
- Public key: `~/.ssh/id_rsa.pub` (can be shared)

## Connect to Remote Server Using Private Key
```bash
ssh -i /path/to/private_key username@host_ip
```
