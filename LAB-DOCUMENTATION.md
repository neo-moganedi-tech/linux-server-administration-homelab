# Linux Server Administration Homelab - Lab Documentation

## 1. Lab Environment

### Objective

Set up an Ubuntu Server virtual machine to be used as the Linux administration environment

### Configuration

* Operating System: Ubuntu Server 24.04 LTS
* Virtualisation: Oracle VirtualBox
* Host System: Windows
* Server Hostname: `linux-server`
* Network Mode: NAT

The Ubuntu Server virtual machine was successfully created and configured as the main Linux administration environment

---

## 2. User and Group Management

### Objective

Create and manage Linux users and groups and establish an administrative group for privilege delegation

### Configuration

An administrative group named:

```text
sysadmins
```

was used to manage administrative privileges.

The `junioradmin` account was used to test administrative access

### Purpose

Using groups provides a scalable way of assigning administrative privileges to users

Instead of configuring permissions individually for each user, administrative access can be delegated through group membership

### Validation

Administrative access was tested using:

```bash
sudo whoami
```

The successful result was:

```text
root
```

---

## 3. Sudo Privilege Configuration

### Objective

Configure sudo to allow members of the administrative group to perform privileged operations

### Configuration

The sudoers configuration included:

```text
%sysadmins ALL=(ALL:ALL) ALL
```

The `%` character identifies `sysadmins` as a group

### Validation

The configuration was tested using:

```bash
sudo whoami
```

Successful output:

```text
root
```

### Troubleshooting

The sudoers configuration initially required correction because the group entry did not include the required `%` prefix

After correcting the configuration, sudo access was successfully validated

---

## 4. File Permissions

### Objective

Understand and configure Linux file ownership and permissions

### Permission Model

Linux permissions are divided into:

* User
* Group
* Others

The available permissions are:

* Read
* Write
* Execute

### Administration

File permissions can be inspected using:

```bash
ls -l
```

Ownership can be modified using:

```bash
chown
```

Permissions can be modified using:

```bash
chmod
```

### Security Consideration

The principle of least privilege was applied when considering access to files and resources

---

## 5. systemd Service Management

### Objective

Use systemd to manage Linux services

### Service Management

Service status can be checked using:

```bash
systemctl status <service>
```

Services can be started using:

```bash
sudo systemctl start <service>
```

Services can be enabled at boot using:

```bash
sudo systemctl enable <service>
```

### Nginx

Nginx was managed as a systemd service and validated as part of the web server configuration

---

## 6. Nginx Web Server

### Objective

Install and configure Nginx as a web server

### Configuration

Nginx was installed on the Ubuntu Server

A custom HTML webpage was created for the project

The webpage identified the server as:

```text
Linux Server Administration Lab
Ubuntu Server 24.04 LTS
```

### Local Validation

The web server was tested locally using:

```bash
curl http://localhost
```

The command successfully returned the custom HTML webpage

### Result

Nginx was successfully installed, configured, and validated

---

## 7. SSH Remote Administration

### Objective

Configure SSH for remote Linux administration

### Configuration

OpenSSH was used to provide remote access to the Ubuntu Server

The guest SSH service uses:

```text
Port 22
```

VirtualBox port forwarding was configured to expose the guest SSH service to the Windows host

```text
Host Port: 2222
Guest Port: 22
```

### Windows Test

The SSH connection was tested from Windows using the forwarded port

Example:

```powershell
ssh -p 2222 junioradmin@127.0.0.1
```

The connection successfully reached the Ubuntu Server

---

## 8. UFW Firewall

### Objective

Configure and validate the Ubuntu firewall

### Validation

The firewall status was checked using:

```bash
sudo ufw status
```

The final configuration showed:

```text
Status: active
```

HTTP traffic was allowed on:

```text
80/tcp
```

This rule was required for the Nginx web server

### Result

UFW was successfully enabled and configured

---

## 9. VirtualBox Networking

### Objective

Configure NAT port forwarding to allow the Windows host to access services running inside the Ubuntu Server virtual machine

### Configuration

The following forwarding rules were configured:

| Service | Host Port | Guest Port |
| ------- | --------: | ---------: |
| SSH     |      2222 |         22 |
| HTTP    |      8080 |         80 |

### SSH

Windows:

```text
127.0.0.1:2222
```

was forwarded to:

```text
Ubuntu Server:22
```

### HTTP

Windows:

```text
127.0.0.1:8080
```

was forwarded to:

```text
Ubuntu Server:80
```

### Result

VirtualBox successfully forwarded traffic from the Windows host to the required services running on Ubuntu Server

---

## 10. Final Validation

### Sudo

```bash
sudo whoami
```

Result:

```text
root
```

### Firewall

```bash
sudo ufw status
```

Result:

```text
Status: active
```

### Local Nginx

```bash
curl http://localhost
```

Result:

Custom HTML webpage returned successfully

### SSH

Windows SSH successfully connected to the Ubuntu Server through the forwarded port

### HTTP

The Windows host successfully accessed the Nginx server through:

```text
http://127.0.0.1:8080
```

### Final Result

The Ubuntu Server administration environment was successfully configured and validated

---

## 11. Troubleshooting

### Sudoers Group Syntax

The sudoers group configuration initially required correction

The correct syntax was:

```text
%sysadmins ALL=(ALL:ALL) ALL
```

The `%` prefix identifies the entry as a group.

### Terminal Pager

Large command output was displayed through a terminal pager

The `q` key was used to exit the pager

### SSH Connectivity

The initial attempt to connect directly to the VirtualBox guest IP from Windows timed out

The issue was resolved by configuring VirtualBox NAT port forwarding

### PowerShell curl

PowerShell can interpret `curl` as an alias for `Invoke-WebRequest`

The actual curl executable can be invoked using:

```powershell
curl.exe
```

### Web Server Testing

The Nginx server was first validated locally on Ubuntu using:

```bash
curl http://localhost
```

After confirming that Nginx was functioning, the service was tested from Windows through the VirtualBox HTTP port forwarding configuration

---

## 12. Conclusion

The Linux Server Administration Homelab successfully demonstrated the configuration and administration of an Ubuntu Server in a virtualised environment

The project covered Linux identity and access management, sudo, file permissions, systemd, Nginx, SSH, firewall configuration, networking, NAT port forwarding, troubleshooting, and technical documentation

The final environment was successfully validated from both the Ubuntu Server and Windows host.
