# Project 3: Cracking Password Hashes with John the Ripper on Kali Linux

## Introduction
In this project, you will learn how to use John the Ripper, a powerful password-cracking tool, to crack password hashes. Cracking password hashes is an essential skill for ethical hackers, as it helps in identifying weak passwords and improving overall security. By the end of this project, you will be able to perform basic password cracking and understand the importance of strong passwords.

## Pre-requisites
- Basic understanding of hashing and encryption concepts.
- Familiarity with using the command line interface (CLI).
- Basic knowledge of password security practices.

## Lab Set-up and Tools

### Diagram
Here is a simple network diagram for this lab setup:
+------------------+ +------------------+
| Attacker | | Target |
| Kali Machine | | System |
| (192.168.1.100) | | (192.168.1.101) |
+------------------+ +------------------+

### Tools
- **Kali Linux**: A Debian-derived Linux distribution designed for digital forensics and penetration testing.
- **John the Ripper**: A fast password cracker included with Kali Linux.
- **Hash files**: Sample files containing password hashes to be cracked.

### Installation
John the Ripper is pre-installed on Kali Linux. You can verify the installation or update it using the following command:
```sh
sudo apt-get update && sudo apt-get install john
```

## Tasks

### Task 1: Basic Password Cracking

Step1: Create a text file named passwords.txt containing a list of password hashes. For example:
```sh
echo '$1$KpixtOtB$VVujBpNkbVnv1BjlBJl6S/' > passwords.txt
```
Step2: Open a terminal on your Kali Linux machine.
Run John the Ripper to crack the password hashes in passwords.txt:
```sh
john passwords.txt
```
Expected Output: John the Ripper should start the cracking process and eventually display the cracked passwords.

### Task 2: Using a Custom Wordlist

Step1: Create a custom wordlist file named wordlist.txt containing potential passwords. For example:
```sh
echo -e "password\n123456\nletmein\nqwerty" > wordlist.txt
```
Step2: Use John the Ripper with the custom wordlist to crack the password hashes:
```sh
john --wordlist=wordlist.txt passwords.txt
```
Expected Output: John the Ripper should use the custom wordlist to crack the passwords and display the results.

### Task 3: Cracking Shadow File Hashes

Step1: Obtain a sample shadow file containing password hashes (ensure you have permission to use this file).
Step2: Extract the password hashes from the shadow file into a new file named shadow_hashes.txt:
```sh
unshadow /etc/passwd /etc/shadow > shadow_hashes.txt
```

Step3: Use John the Ripper to crack the password hashes in shadow_hashes.txt:
```sh
john shadow_hashes.txt
```
Expected Output: John the Ripper should start the cracking process and eventually display the cracked passwords.

### Task 4: Incremental Mode Cracking
Step1: Use John the Ripper in incremental mode to attempt a brute-force crack on the password hashes:
```sh
john --incremental passwords.txt
```
Expected Output: John the Ripper should start the brute-force cracking process and display the cracked passwords as it finds them.

### Task 5: Cracking Passwords with Rules

Step1: Use John the Ripper with a rules-based approach to crack the password hashes. For example, use the default rules provided by John the Ripper:
```sh
john --rules passwords.txt
```
Expected Output: John the Ripper should apply the rules and attempt to crack the passwords, displaying any successful results.

Task 6: Analyzing Cracked Passwords

Step1: After cracking the passwords, analyze the results to identify common patterns and weaknesses.
Step2: Use the john --show command to display all cracked passwords:
```sh
john --show passwords.txt
```
Expected Output: A detailed list of all cracked passwords and their corresponding hashes, highlighting common password patterns.


## Additional Resources
John the Ripper Documentation
Kali Linux Documentation
Password Security Best Practices
Hashcat vs John the Ripper

This project will help you understand how to crack password hashes using John the Ripper on Kali Linux, highlighting the importance of strong password policies and secure hashing algorithms.



