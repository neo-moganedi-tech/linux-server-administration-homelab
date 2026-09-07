# Evidence

This directory contains the screenshots captured during the Linux Server Administration Homelab

The evidence documents the configuration, administration, monitoring, security, web server deployment, and scripting tasks completed on the Ubuntu Server 24.04 LTS virtual machine

## Evidence Files

### 1. System Information

**File:** `01-system-info.png`

This screenshot provides evidence of the Ubuntu Server environment and system configuration used throughout the lab

It demonstrates the Linux server operating system and confirms the server environment used for the administration tasks

---

### 2. User Groups

**File:** `02-user-groups.png`

This screenshot provides evidence of Linux user and group administration

The lab included the creation and management of users and groups, including the `sysadmins` administrative group

Group-based administration was used to manage access and administrative privileges

---

### 3. File Permissions

**File:** `03-permissions.png`

This screenshot provides evidence of Linux file ownership and permission management

The lab covered the Linux permission model, including:

- Read permissions
- Write permissions
- Execute permissions
- User ownership
- Group ownership

File permissions are an important part of Linux security and access control

---

### 4. Nginx Status

**File:** `04-nginx-status.png`

This screenshot provides evidence that the Nginx web server was installed and operating as a system service

Nginx was used to host the custom webpage created for the Linux Server Administration Homelab

The service was managed and validated using systemd

---

### 5. Firewall

**File:** `05-firewall.png`

This screenshot provides evidence of the UFW firewall configuration

The firewall was enabled and verified as active

HTTP traffic on port `80` was allowed to support the Nginx web server

The firewall configuration helped control network access to services running on the Ubuntu Server

---

### 6. Logs

**File:** `06-logs.png`

This screenshot provides evidence of Linux system and service log monitoring

Logs were reviewed as part of the administration and troubleshooting process

Log analysis is an important Linux administration skill because it can be used to identify service issues, authentication activity, system events, and other problems

---

### 7. Web Server

**File:** `07-web-server.png`

This screenshot provides evidence of the completed Nginx web server configuration

A custom webpage was created for the project and served by Nginx

The webpage identifies the environment as:

- `Linux Server Administration Lab Ubuntu Server 24.04 LTS`

### 8. Bash Script

File: `08-bash-script.png`

This screenshot provides evidence of Bash scripting performed during the lab

The script demonstrates the use of the Linux command line and Bash automation to perform administration-related tasks

Bash scripting was included to demonstrate basic automation and command-line administration skills
