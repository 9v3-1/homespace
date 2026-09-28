# Initial Nmap Reconnaissance

## Objective

Identify TCP services exposed by the Ubuntu Server to the Kali Linux testing machine.

## Command

```bash
nmap 192.168.56.101
```

### Results

| Port   | State | Service |
| ------ | ----- | ------- |
| 22/tcp | open  | SSH     |
| 80/tcp | open  | HTTP    |

The scan reported 998 closed TCP ports among the default 1,000 ports scanned.

## Service Enumeration

The following command was used to identify service versions:

```bash
nmap -sV 192.168.56.101
```

### Results

* **22/tcp:** OpenSSH 10.2p1 Ubuntu 2ubuntu3.6
* **80/tcp:** nginx 1.28.3 (Ubuntu)

## Observations

The Ubuntu server currently exposes two network services to the Kali testing machine:

1. SSH on TCP port 22
2. HTTP on TCP port 80

At this stage, the scan identifies exposed services but does not by itself establish that either service is vulnerable.

## Next Step

Further enumeration will focus on the HTTP service and the SSH configuration before making any security changes.
