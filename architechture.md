# homespace architecture.

## Overview

This homelab consists of two VirtualBox virtual machines:

* **Ubuntu Server** — server/target environment
* **Kali Linux** — security testing environment

Both VMs use a VirtualBox Host-only Network (`vboxnet0`) for private communication.

## Network

| Machine       | Role             | Network          |
| ------------- | ---------------- | ---------------- |
| Ubuntu Server | Server           | `192.168.56.101` |
| Kali Linux    | Security testing | `192.168.56.x`   |

The VMs also have NAT connectivity for Internet access and system updates.

## Current Connectivity

Kali Linux can successfully:

* Reach Ubuntu Server over the private network
* Connect to Ubuntu Server using SSH on port 22

## SSH

SSH is enabled on the Ubuntu Server and can be accessed from Kali using:

```bash
ssh <username>@192.168.56.101
```

## Objective

The goal of this lab is to build my practical Linux and cybersecurity skills by:

1. Configuring and administering the Ubuntu server
2. Learning networking and network services
3. Performing security testing from Kali Linux
4. Identifying vulnerabilities in the lab environment
5. Hardening the Ubuntu server
6. Re-testing the system after security changes
7. Documenting the process and results
