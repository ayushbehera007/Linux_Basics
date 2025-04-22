# Linux Package Managers and Service Management

## APT (Debian/Ubuntu based systems)

APT (Advanced Package Tool) is used in Debian and Ubuntu-based distributions.

### Common Commands

| Command | Description |
|---------|-------------|
| `sudo apt update` | Updates the list of available packages. |
| `sudo apt upgrade` | Upgrades all upgradable packages. |
| `sudo apt install <package>` | Installs a new package. |
| `sudo apt remove <package>` | Removes a package. |
| `sudo apt purge <package>` | Removes a package and its config files. |
| `sudo apt autoremove` | Removes unnecessary dependencies. |
| `apt search <package>` | Searches for a package. |
| `apt show <package>` | Shows details of a package. |

---

## YUM (RHEL/CentOS based systems)

YUM (Yellowdog Updater Modified) is used in Amazon Linux 2, RedHat and CentOS distributions.

### Common Commands

| Command | Description |
|---------|-------------|
| `sudo yum check-update` | Checks for updates. |
| `sudo yum update` | Updates all packages. |
| `sudo yum install <package>` | Installs a new package. |
| `sudo yum remove <package>` | Removes a package. |
| `sudo yum list installed` | Lists installed packages. |
| `yum search <package>` | Searches for a package. |
| `yum info <package>` | Shows package information. |

---

## Zypper (openSUSE based systems)

Zypper is the package manager for openSUSE and SUSE Linux Enterprise.

### Common Commands

| Command | Description |
|---------|-------------|
| `sudo zypper refresh` | Refreshes the repository metadata. |
| `sudo zypper update` | Updates all packages. |
| `sudo zypper install <package>` | Installs a new package. |
| `sudo zypper remove <package>` | Removes a package. |
| `zypper search <package>` | Searches for a package. |
| `zypper info <package>` | Shows details about a package. |

---

## systemctl (Systemd service management)

`systemctl` is used to control the systemd system and service manager.

### Common Commands

| Command | Description |
|---------|-------------|
| `systemctl start <service>` | Starts a service. |
| `systemctl stop <service>` | Stops a service. |
| `systemctl restart <service>` | Restarts a service. |
| `systemctl status <service>` | Shows the status of a service. |
| `systemctl enable <service>` | Enables a service to start on boot. |
| `systemctl disable <service>` | Disables a service from starting on boot. |
| `systemctl is-enabled <service>` | Checks if a service is enabled. |
