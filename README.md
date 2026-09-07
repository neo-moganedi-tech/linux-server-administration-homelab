# Linux Server Administration Homelab

## Project Overview

A hands-on Ubuntu Server 24.04 LTS lab focused on Linux server administration, user and group management, sudo privilege configuration, file permissions, systemd services, Nginx, SSH, UFW firewall configuration, networking, and troubleshooting

The lab was completed in a virtualised environment using Oracle VirtualBox and was designed to develop practical experience administering and validating a Linux server

## Objectives

* Configure Ubuntu Server 24.04 LTS
* Create and manage Linux users and groups
* Configure administrative privileges using sudo
* Configure and validate file permissions
* Manage Linux services using systemd
* Install and configure Nginx
* Create and host a custom HTML webpage
* Configure and test SSH remote administration
* Configure UFW firewall rules
* Configure VirtualBox NAT networking
* Configure SSH and HTTP port forwarding
* Test connectivity from a Windows host
* Troubleshoot configuration and connectivity issues
* Document the configuration and technical evidence

## Technologies & Tools

* Ubuntu Server 24.04 LTS
* Oracle VirtualBox
* Linux Command Line
* Bash
* systemd
* sudo
* Nginx
* OpenSSH
* UFW
* NAT Networking
* Port Forwarding
* Windows PowerShell

## Lab Environment

The lab consisted of an Ubuntu Server 24.04 LTS virtual machine running inside Oracle VirtualBox

The Windows host system was used to perform remote administration and connectivity testing

The Ubuntu server was configured with the hostname:

```text
linux-server
```

## User and Group Management

Linux users and groups were configured as part of the administration process

A dedicated administrative group named `sysadmins` was used to manage sudo privileges

The `junioradmin` account was used to validate administrative access

## Sudo Configuration

Administrative privileges were configured using the sudoers configuration

The administrative group was configured using:

```text
%sysadmins ALL=(ALL:ALL) ALL
```

Sudo access was validated using:

```bash
sudo whoami
```

The successful result was:

```text
root
```

This confirmed that the configured administrative privileges were functioning correctly.

## File Permissions

Linux file ownership and permissions were reviewed and configured during the lab.

The project covered the Linux permission model, including:

* Read
* Write
* Execute
* User ownership
* Group ownership
* Other permissions

The principle of least privilege was applied when managing access to files and resources.

## systemd Services

systemd was used to manage and validate Linux services.

Service management included checking service status and ensuring required services were available for the lab environment.

Nginx was managed as a systemd service.

## Nginx Web Server

Nginx was installed and configured as the web server.

A custom HTML webpage was created for the project.

The webpage identified the environment as a Linux Server Administration Lab running Ubuntu Server 24.04 LTS.

The local web server was tested using:

```bash
curl http://localhost
```

The server successfully returned the custom webpage.

## SSH Configuration

OpenSSH was configured to provide remote administration access to the Ubuntu Server.

SSH uses port `22` on the Ubuntu guest.

Because the virtual machine used NAT networking, VirtualBox port forwarding was configured to allow the Windows host to connect to the server.

The SSH forwarding configuration was:

```text
Host Port: 2222
Guest Port: 22
```

SSH was successfully tested from the Windows host.

## UFW Firewall

UFW was used to manage firewall access on the Ubuntu Server.

The firewall was verified as active using:

```bash
sudo ufw status
```

HTTP traffic on port `80` was allowed to support the Nginx web server.

## Networking Configuration

VirtualBox NAT networking was used for the Ubuntu Server.

Port forwarding was configured as follows:

| Service | Host Port | Guest Port |
| ------- | --------: | ---------: |
| SSH     |      2222 |         22 |
| HTTP    |      8080 |         80 |

This allowed the Windows host to access services running inside the Ubuntu virtual machine.

## Testing & Troubleshooting

The lab included several troubleshooting exercises.

Issues encountered during the project included:

* Correcting sudoers group syntax
* Understanding Linux terminal pagers
* Troubleshooting SSH connectivity
* Configuring VirtualBox NAT port forwarding
* Understanding PowerShell's `curl` behaviour
* Validating firewall configuration
* Testing Nginx locally and from the Windows host

The troubleshooting process involved checking configuration, validating services locally, testing networking, and confirming connectivity from the client system.

## Evidence

Screenshots and supporting evidence are provided in the `evidence` directory.

The evidence demonstrates:

* Sudo privilege validation
* UFW firewall configuration
* SSH connectivity
* VirtualBox port forwarding
* Nginx web server validation

## Key Skills Demonstrated

* Linux Server Administration
* Ubuntu Server Administration
* User and Group Management
* Sudo and Privilege Management
* File Permissions
* systemd Service Management
* Nginx
* SSH
* UFW Firewall
* Networking
* NAT and Port Forwarding
* Bash
* Troubleshooting
* Command-Line Administration
* Technical Documentation

## What I Learned

This lab provided practical experience administering an Ubuntu Server in a virtualised environment

I developed a stronger understanding of Linux users and groups, privilege delegation, file permissions, service management, firewall configuration, SSH, and network connectivity

The project also reinforced the importance of troubleshooting systematically by validating each layer of the environment, from the Linux configuration and services through to firewall rules, virtual networking, and remote client connectivity
