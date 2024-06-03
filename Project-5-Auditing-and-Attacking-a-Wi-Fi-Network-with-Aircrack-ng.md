# Project 5: Auditing and Attacking a Wi-Fi Network with Aircrack-ng on Kali Linux

## Introduction
In this project, you will learn how to use Aircrack-ng, a suite of tools for auditing and attacking Wi-Fi networks. This project will help you understand the security vulnerabilities in Wi-Fi networks and how to exploit them ethically. By the end of this project, you will be able to perform network discovery, capture packets, and crack WEP/WPA/WPA2 passwords.

## Pre-requisites
- Basic understanding of wireless networking concepts (SSID, BSSID, channels).
- Familiarity with using the command line interface (CLI).
- Basic knowledge of Wi-Fi security protocols (WEP, WPA, WPA2).

## Lab Set-up and Tools

### Diagram
Here is a simple network diagram for this lab setup:

+------------------+ +------------------+
| Attacker | | Wi-Fi Router |
| Kali Machine |<----->| (Target Network)|
| (192.168.1.100) | | (192.168.1.1) |
+------------------+ +------------------+
|
|
+------------------+
| Target Device |
| (Wi-Fi Client) |
| (192.168.1.101)|
+------------------+


### Tools
- **Kali Linux**: A Debian-derived Linux distribution designed for digital forensics and penetration testing.
- **Aircrack-ng**: A suite of tools for Wi-Fi network auditing and penetration testing (pre-installed on Kali Linux).
- **Wi-Fi Adapter**: A compatible Wi-Fi adapter that supports monitor mode.

### Installation
Aircrack-ng is pre-installed on Kali Linux. You can verify the installation or update it using the following command:
```sh
sudo apt-get update && sudo apt-get install aircrack-ng
```
