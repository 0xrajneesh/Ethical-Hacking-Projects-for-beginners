# Project 2: Penetration Testing a Vulnerable Web Application using OWASP Juice Shop on Kali Linux

## Introduction
In this project, you will learn how to use various tools to perform penetration testing on a vulnerable web application, OWASP Juice Shop. OWASP Juice Shop is a deliberately insecure web application for educational purposes. This project will help you understand common web vulnerabilities and how to exploit them ethically.

## Pre-requisites
- Basic understanding of web application concepts (HTTP, HTTPS, web servers).
- Familiarity with using the command line interface (CLI).
- Basic knowledge of web development technologies (HTML, JavaScript, etc.).

## Lab Set-up and Tools

### Diagram
Here is a simple network diagram for this lab setup:

+------------------+ +------------------+
| Attacker | | Vulnerable App |
| Kali Machine |<----->| (OWASP Juice |
| (192.168.1.100) | | Shop) |
+------------------+ +------------------+


### Tools
- **Kali Linux**: A Debian-derived Linux distribution designed for digital forensics and penetration testing.
- **OWASP Juice Shop**: A vulnerable web application for educational purposes.
- **Burp Suite**: An integrated platform for performing security testing of web applications (pre-installed on Kali Linux).

### Installation
#### OWASP Juice Shop
You can set up OWASP Juice Shop on your local machine using Docker:
1. Install Docker on your Kali Linux machine:
   ```sh
   sudo apt-get update
   sudo apt-get install docker.io
   sudo systemctl start docker
   sudo systemctl enable docker
   ```

2. Pull the OWASP Juice Shop Docker image:
   ```
   sudo docker pull bkimminich/juice-shop
   ```
3. Run the OWASP Juice Shop container:
  ```
  sudo docker run -d -p 3000:3000 bkimminich/juice-shop
  ```
4. Access the OWASP Juice Shop web application by navigating to http://localhost:3000 in your web browser.

## Tasks

### Task 1: Identify Open Ports
Step1: Open a terminal on your Kali Linux machine.
Step2: Scan for open ports on the machine running OWASP Juice Shop. Replace ``192.168.1.100`` with the IP address of your OWASP Juice Shop instance.
  ```
  nmap 192.168.1.100
  ```
Expected Output: A list of open ports on the OWASP Juice Shop server.

### Task 2: SQL Injection

Step1: Open Burp Suite on your Kali Linux machine.
Step2: Configure your browser to use Burp Suite as a proxy ``(127.0.0.1:8080)``.
Step3: Intercept a login request and attempt an SQL injection attack. For example, use ``' OR '1'='1`` as the username and password.
Expected Output: Access to the application with an SQL injection payload.

### Task 3: Cross-Site Scripting (XSS)
Step1: Navigate to a page in OWASP Juice Shop where user input is reflected (e.g., the search bar).
Step2: Enter a basic XSS payload such as ``<script>alert('XSS')</script>`` into the input field.
Expected Output: An alert box should appear, indicating that the XSS attack was successful.

### Task 4: File Upload Vulnerability
Step1: Navigate to a page in OWASP Juice Shop that allows file uploads (e.g., profile picture upload).
Step2: Attempt to upload a malicious file (e.g., a PHP reverse shell script).
Expected Output: Verify if the file upload feature is vulnerable by trying to access or execute the uploaded file.

### Task 5: Directory Traversal
Step1: Use Burp Suite to intercept a request to the server.
Step2: Modify the request to include a directory traversal payload. For example, ``../../../etc/passwd``.
Expected Output: Access to files outside the web root, such as /etc/passwd, indicating a directory traversal vulnerability.

### Task 6: Cross-Site Request Forgery (CSRF)
Step1: Create a malicious HTML form that performs an action on behalf of an authenticated user (e.g., changing the user's email address).
Step2: Load the form in your browser while authenticated to OWASP Juice Shop.
Expected Output: The action is performed without the user's consent, demonstrating a CSRF vulnerability.

## Additional Resources
OWASP Juice Shop Documentation
Burp Suite Documentation
Web Security Academy by PortSwigger
Kali Linux Documentation

This project will help you understand common web vulnerabilities and how to exploit them ethically using Kali Linux and OWASP Juice Shop.

