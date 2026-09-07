# Linux Server Administration Lab — Commands Reference

This document contains the main Linux commands used during the Linux Server Administration Homelab, along with their purpose

---

## System Information

### Display operating system information

```bash
lsb_release -a
```

**Purpose:** Displays the Ubuntu distribution, release, and version information

### Display kernel information

```bash
uname -a
```

**Purpose:** Displays kernel and system information

### Display hostname

```bash
hostname
```

**Purpose:** Displays the server hostname

### Display IP addressing information

```bash
ip addr
```

**Purpose:** Displays network interfaces and assigned IP addresses

---

## Users and Groups

### Create a user

```bash
sudo adduser junioradmin
```

**Purpose:** Creates a new local user account

### Add a user to a group

```bash
sudo usermod -aG sysadmins junioradmin
```

**Purpose:** Adds `junioradmin` to the `sysadmins` group without removing existing group memberships

### Create an administrative group

```bash
sudo groupadd sysadmins
```

**Purpose:** Creates the `sysadmins` group

### Display the current user's identity

```bash
whoami
```

**Purpose:** Displays the username of the currently logged-in user

### Display user and group memberships

```bash
groups
```

**Purpose:** Displays the groups associated with the current user

### Display detailed user and group information

```bash
id junioradmin
```

**Purpose:** Displays the UID, GID, and group memberships for `junioradmin`

---

## Sudo Administration

### Edit the sudoers configuration

```bash
sudo visudo
```

**Purpose:** Safely edits the system sudo configuration

### Test sudo privileges

```bash
sudo whoami
```

**Purpose:** Verifies that the user can execute commands with administrative privileges

Expected result:

```text
root
```

---

## File and Directory Management

### Create a directory

```bash
sudo mkdir /var/www/html
```

**Purpose:** Creates the directory used for web content

### Create a file

```bash
sudo touch filename
```

**Purpose:** Creates an empty file

### Edit a file with Nano

```bash
sudo nano filename
```

**Purpose:** Opens a file for editing using the Nano text editor

### Display file contents

```bash
cat filename
```

**Purpose:** Displays the contents of a file

### List files and directories

```bash
ls
```

**Purpose:** Lists files and directories in the current location

### List detailed file information

```bash
ls -l
```

**Purpose:** Displays file permissions, ownership, size, and modification information

---

## File Permissions

### Change file permissions

```bash
sudo chmod 644 filename
```

**Purpose:** Sets read/write permissions for the owner and read-only permissions for group and other users

### Change file ownership

```bash
sudo chown username:groupname filename
```

**Purpose:** Changes the owner and group associated with a file

### Display file permissions

```bash
ls -l filename
```

**Purpose:** Verifies the permissions and ownership assigned to a file

---

## Package Management

### Update package information

```bash
sudo apt update
```

**Purpose:** Updates the local package repository information

### Upgrade installed packages

```bash
sudo apt upgrade
```

**Purpose:** Installs available updates for installed packages

### Install a package

```bash
sudo apt install package-name
```

**Purpose:** Installs a specified package

---

## Nginx Web Server

### Install Nginx

```bash
sudo apt install nginx
```

**Purpose:** Installs the Nginx web server

### Check Nginx service status

```bash
sudo systemctl status nginx
```

**Purpose:** Displays the current status of the Nginx service

### Start Nginx

```bash
sudo systemctl start nginx
```

**Purpose:** Starts the Nginx web server

### Enable Nginx at boot

```bash
sudo systemctl enable nginx
```

**Purpose:** Configures Nginx to start automatically when the server boots

### Restart Nginx

```bash
sudo systemctl restart nginx
```

**Purpose:** Restarts Nginx after configuration or content changes

### Test the website locally

```bash
curl http://localhost
```

**Purpose:** Sends an HTTP request to the local Nginx server to verify that the website is responding

---

## systemd Services

### Check a service

```bash
sudo systemctl status nginx
```

**Purpose:** Checks whether the specified systemd service is running

### Start a service

```bash
sudo systemctl start nginx
```

**Purpose:** Starts a systemd service

### Stop a service

```bash
sudo systemctl stop nginx
```

**Purpose:** Stops a systemd service

### Restart a service

```bash
sudo systemctl restart nginx
```

**Purpose:** Restarts a systemd service

### Enable a service

```bash
sudo systemctl enable nginx
```

**Purpose:** Configures a service to start automatically during system boot

---

## SSH

### Install OpenSSH server

```bash
sudo apt install openssh-server
```

**Purpose:** Installs the SSH server used for remote administration

### Check SSH service status

```bash
sudo systemctl status ssh
```

**Purpose:** Verifies that the SSH service is running

### Start SSH

```bash
sudo systemctl start ssh
```

**Purpose:** Starts the SSH service

### Enable SSH at boot

```bash
sudo systemctl enable ssh
```

**Purpose:** Configures SSH to start automatically when the server boots

### Connect to the server remotely

```bash
ssh username@server-ip
```

**Purpose:** Establishes a secure remote shell session with the Linux server

---

## UFW Firewall

### Check firewall status

```bash
sudo ufw status
```

**Purpose:** Displays the current UFW firewall status and configured rules

### Allow HTTP traffic

```bash
sudo ufw allow 80/tcp
```

**Purpose:** Allows incoming HTTP traffic on TCP port 80

### Allow SSH traffic

```bash
sudo ufw allow 22/tcp
```

**Purpose:** Allows incoming SSH traffic on TCP port 22

### Enable UFW

```bash
sudo ufw enable
```

**Purpose:** Activates the UFW firewall

### Display detailed firewall status

```bash
sudo ufw status verbose
```

**Purpose:** Displays firewall rules and additional configuration details

---

## Logs

### View system logs

```bash
sudo journalctl
```

**Purpose:** Displays logs collected by the systemd journal

### View logs for a specific service

```bash
sudo journalctl -u nginx
```

**Purpose:** Displays logs generated by the Nginx service

### View recent service logs

```bash
sudo journalctl -u nginx -n 50
```

**Purpose:** Displays the most recent 50 log entries for Nginx

---

## Process Management

### Display running processes

```bash
ps aux
```

**Purpose:** Displays currently running processes

### Display processes interactively

```bash
top
```

**Purpose:** Provides a real-time view of running processes and system resource usage

---

## Disk and Storage

### Display disk usage

```bash
df -h
```

**Purpose:** Displays filesystem disk usage in human-readable format

### Display directory size

```bash
du -sh directory
```

**Purpose:** Displays the total size of a directory

---

## Network Testing

### Test local network connectivity

```bash
ping 127.0.0.1
```

**Purpose:** Tests basic network connectivity using the local loopback interface

### Test HTTP connectivity

```bash
curl http://localhost
```

**Purpose:** Verifies that the local web server responds to HTTP requests

### Test a server port

```bash
ss -tulpn
```

**Purpose:** Displays listening TCP/UDP ports and the processes using them

---

## Bash

### Create a Bash script

```bash
nano script.sh
```

**Purpose:** Creates or edits a Bash script

### Make a script executable

```bash
chmod +x script.sh
```

**Purpose:** Grants execute permission to the Bash script

### Run a Bash script

```bash
./script.sh
```

**Purpose:** Executes the Bash script from the current directory

### Run a script using Bash

```bash
bash script.sh
```

**Purpose:** Executes a Bash script using the Bash interpreter

---

## Administrative Verification

### Display current user

```bash
whoami
```

**Purpose:** Confirms which account is currently being used

### Display current working directory

```bash
pwd
```

**Purpose:** Displays the current directory

### Display command history

```bash
history
```

**Purpose:** Displays previously executed shell commands

---

## Summary

The commands in this reference cover the main administration tasks performed during the lab:

- System information
- User and group administration
- Sudo configuration
- File permissions
- Package management
- Nginx web server administration
- systemd service management
- SSH administration
- UFW firewall configuration
- Log analysis
- Network testing
- Bash scripting
- Basic Linux troubleshooting
