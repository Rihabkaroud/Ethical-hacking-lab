# Ethical Hacking Laboratory

## Overview

This project documents the practical exercises completed while learning ethical hacking and penetration testing using Kali Linux, Metasploitable 2, Hack The Box, and common security assessment tools.

The objective was to understand the complete penetration testing lifecycle, from environment setup to reconnaissance, scanning, enumeration, exploitation, and shell access.

# Laboratory Environment

## Attacker

- Kali Linux
- VirtualBox

### Network Configuration

Adapter 1

- Internal Network
- Interface: eth0
- IP Range: 192.168.1.0/24

Adapter 2

- NAT
- Interface: eth1
- Internet Access
- IP Range: 10.0.3.0/24

### Network Issue

The default route initially pointed to the internal network:

default via 192.168.1.1 dev eth0

Since this gateway has no Internet connectivity, external hosts could not be reached.

Diagnosis:

ip a
ip route
ping 10.0.3.1
ping google.com

Solution:

sudo ip route del default via 192.168.1.1


# Tools Installed

- Impacket
- Nmap
- Wireshark
- Burp Suite
- Nikto
- Nessus
- Metasploit Framework

# Network Discovery

## Custom Bash Scanner

A simple Bash script was written to discover live hosts.

./ipsweep.sh 192.168.1


Output was redirected into a text file.


./ipsweep.sh 192.168.1 > iplist.txt


## Nmap Host Discovery

nmap -sn 192.168.1.0/24


# Reconnaissance

## Hunter.io

Used for collecting publicly available employee email addresses associated with a target domain.

Example:

tesla.com

## Breach Parse

A password intelligence tool used to search breached credentials associated with a specific domain.


# Network Traffic Analysis

Wireshark was used to inspect network communications between the virtual machine and Tesla's public website.

Observed hosts included:

- Google Cloud
- CDN providers
- Google DNS
- Tesla infrastructure

Key observations:

- Three-way TCP handshake
- Multiple CDN endpoints
- Server infrastructure distributed across several providers

# Port Scanning

Several Nmap scan techniques were explored

Examples:

nmap -sS
nmap -sn
nmap -T4 -A
nmap -sU

Nmap NSE scripts were also used for service enumeration.


# Enumeration

## HTTP (Port 80)

The target hosted an Apache web server.

Enumeration included:

- Server header inspection
- Hidden directory discovery
- Source code inspection
- Directory brute forcing using DirBuster

Exposed applications included:

- DVWA
- phpMyAdmin
- TWiki
- Mutillidae
- WebDAV

## SSH (Port 22)

OpenSSH version information was identified for vulnerability assessment.

## SMB (Port 139)

SMB shares were enumerated using smbclient.

Anonymous access successfully revealed several shared folders.

# Vulnerability Assessment

The following tools were practiced:

- Nessus
- Nikto
- Metasploit

Each tool was used to identify exposed services and known vulnerabilities.

# Hack The Box

A vulnerable machine was selected and analyzed.

Activities included:

- Port scanning
- Service fingerprinting
- DNS manipulation
- SFTP access
- Credential discovery

# Exploitation

The following attack techniques were practiced:

## Reverse Shell

Implemented using Netcat.

## Bind Shell

Basic shell interaction between attacker and target.

## Apache Exploitation

Version-based exploitation using publicly known vulnerabilities.

## Responder

Captured authentication traffic on the local network.

# Skills Demonstrated

- Linux Administration
- Bash Scripting
- Network Enumeration
- TCP/IP Analysis
- Wireshark
- Nmap
- SMB Enumeration
- Web Enumeration
- Metasploit
- Nessus
- Burp Suite
- Reverse Shells
- Penetration Testing Methodology
