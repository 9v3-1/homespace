# HomeSpace Homelab

A small, virtualized cybersecurity homelab running on a Thinkpad. This repository documents the design, configuration, experiments, and lessons learned while building a practical environment for networking, Linux administration, monitoring, and defensive security.

> **Purpose:** Learn by building, breaking, monitoring, hardening, and documenting a controlled lab environment.

## Goals

- Build and manage Linux servers using Ubuntu Server.
- Practice SSH administration, users, groups, permissions, and sudo.
- Design an isolated internal network with static IP addresses, DNS, and DHCP.
- Host a small website inside the lab.
- Collect and review authentication and system logs.
- Detect failed SSH logins and other suspicious activity.
- Apply security hardening, including SSH keys, disabling root login, and firewall rules.
- Use Kali Linux for controlled attack simulations and validation of defensive controls.
- Create dashboards and reports that show the health and security of the environment.

## Lab Scope

This project is intended for a private, isolated, and authorized lab environment. All testing and attack simulations will be performed only against systems that I own or have explicit permission to test.

The lab will run as a small virtualized environment on a laptop. The exact number of virtual machines may change as the project grows.

## Planned Environment

| Component | Purpose |
| --- | --- |
| Ubuntu Server | Linux administration, SSH, web hosting, logging, and security services |
| Kali Linux | Authorized security testing and attack simulations |
| Internal virtual network | Segmentation and communication between lab systems |
| Small web server | Practice deploying and securing a website |
| Logging/monitoring system | Collect authentication and system events and identify suspicious behavior |
| Host laptop | Runs the virtual machines and provides the isolated lab platform |

## Network Plan

The internal network will focus on predictable and well-documented addressing and name resolution.

Planned services include:

- Static IP addresses for infrastructure systems.
- DHCP for approved dynamic clients.
- Internal DNS for resolving lab hostnames.
- Documented network ranges, gateways, and reserved addresses.
- Separation between the lab network and the normal home network where practical.

Example host inventory:

| Hostname | Role | Address | Status |
| --- | --- | --- | --- |
| `server01` | Ubuntu Server | To be assigned | Planned |
| `kali` | Security testing workstation | To be assigned | Planned |
| `dns01` | DNS/DHCP services | To be assigned | Planned |
| `web01` | Website host | To be assigned | Planned |

> Addresses and hostnames will be updated as the lab is implemented.

## Security and Hardening

The baseline hardening plan includes:

- Use SSH keys instead of password-only authentication where possible.
- Disable direct root SSH login.
- Use least-privilege user accounts and carefully managed `sudo` access.
- Configure host-based firewall rules with only required services exposed.
- Keep Ubuntu packages and security updates current.
- Remove or disable unnecessary services.
- Use strong passwords and protect private keys.
- Restrict administrative access to the internal lab network.
- Review file ownership and permissions regularly.
- Record configuration changes and security decisions.

Hardening will be performed incrementally, with each change tested and documented so that access is not accidentally lost.

## Logging and Detection

The lab will collect and review security-relevant events, including:

- Successful and failed SSH authentication attempts.
- Sudo and privilege-escalation activity.
- User and group changes.
- Firewall events.
- Service starts, stops, and failures.
- Package installation and update activity.
- Web server access and error logs.
- Unexpected processes, connections, or configuration changes.

Detection exercises will include identifying:

- Repeated failed SSH logins.
- Login attempts from unexpected systems.
- Suspicious privilege use.
- Unusual network connections.
- Changes to important files or services.
- Abnormal web requests and probing activity.

Possible tooling will be evaluated as the lab develops. The initial focus will be on understanding native Linux logs and command-line analysis before adding dashboards or larger monitoring platforms.

## Attack Simulations

Kali Linux will be used to run controlled simulations against the lab systems. Example exercises may include:

- Network discovery and service enumeration.
- SSH authentication testing in the isolated lab.
- Web server reconnaissance.
- Testing firewall exposure and segmentation.
- Generating failed-login events and confirming that they are detected.
- Validating hardening changes and documenting the results.

Every exercise should have:

1. A defined objective.
2. A target system and approved scope.
3. A safe test procedure.
4. Evidence such as logs, screenshots, or command output.
5. Findings and recommended improvements.
6. Cleanup and verification steps.

## Dashboards and Reports

The project will include simple dashboards and written reports covering:

- System availability and resource usage.
- Network services and exposed ports.
- Authentication activity.
- Failed-login trends.
- Firewall and web-server events.
- Security exercise results.
- Hardening status and outstanding tasks.

Reports will prioritize clear evidence and repeatable observations over complexity.

## Suggested Repository Structure

```text
.
├── README.md
├── docs/
│   ├── architecture.md
│   ├── network-plan.md
│   ├── hardening-checklist.md
│   └── exercises/
├── configs/
│   ├── ssh/
│   ├── firewall/
│   ├── dns/
│   └── dhcp/
├── scripts/
│   ├── setup/
│   ├── monitoring/
│   └── validation/
├── logs/
│   └── .gitkeep
├── reports/
│   └── .gitkeep
└── diagrams/
```

Do not commit passwords, private SSH keys, tokens, sensitive logs, or other secrets. Use sanitized examples, environment variables, and a suitable `.gitignore` instead.

## Project Workflow

1. Plan the network and virtual machines.
2. Build the Ubuntu Server baseline.
3. Configure users, SSH, permissions, updates, and firewall rules.
4. Add DNS, DHCP, and internal host naming.
5. Deploy the small website.
6. Centralize or organize authentication and system logs.
7. Add detection rules and monitoring.
8. Use Kali Linux to perform controlled validation exercises.
9. Record findings, remediate weaknesses, and retest.
10. Publish a concise report for each major exercise.

## Current Status

- [x] Create the project repository.
- [ ] Define the virtual machine layout.
- [ ] Document the internal network and IP plan.
- [ ] Deploy Ubuntu Server.
- [ ] Configure SSH and administrative access.
- [ ] Configure firewall rules.
- [ ] Configure DNS and DHCP.
- [ ] Host the first internal website.
- [ ] Collect authentication and system logs.
- [ ] Add failed-SSH-login detection.
- [ ] Add monitoring dashboards.
- [ ] Run the first Kali Linux validation exercise.
- [ ] Publish the first lab report.

## Learning Notes

This repository is both a lab record and a learning journal. Each change should explain what was done, why it was done, how it was tested, and what was learned.

## Disclaimer

This project is for education, defensive security practice, and authorized testing only. Do not scan, attack, or attempt to access systems, networks, accounts, or data without explicit permission.
