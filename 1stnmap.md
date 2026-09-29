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

# HTTP Enumeration

## Objective

Further enumerate the HTTP service discovered on TCP port 80.

## HTTP Headers

Command:

```bash
curl -I http://192.168.56.101
```

The server returned:

```text
HTTP/1.1 200 OK
Server: nginx/1.28.3 (Ubuntu)
Content-Type: text/html
Content-Length: 615
Connection: keep-alive
```

The response also contained `Last-Modified`, `ETag`, and `Accept-Ranges` headers.

### Observation

The HTTP `Server` header discloses the Nginx version and Ubuntu platform:

```text
nginx/1.28.3 (Ubuntu)
```

This provides version information to clients and therefore represents useful reconnaissance information. Version disclosure alone does not establish that the software is vulnerable.

## HTTP Methods

Command:

```bash
nmap -p 80 --script http-methods 192.168.56.101
```

Nmap reported:

```text
GET
HEAD
```

### Observation

The HTTP service currently supports the `GET` and `HEAD` methods. No additional methods were reported by the Nmap script.

## Current Attack Surface

```text
TCP/22 → SSH → OpenSSH 10.2p1
TCP/80 → HTTP → nginx 1.28.3
```

At this stage, the server is running the default Nginx website and no vulnerability has been established.
