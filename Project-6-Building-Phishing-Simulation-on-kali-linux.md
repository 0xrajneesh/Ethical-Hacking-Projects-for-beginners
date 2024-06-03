# Project 6: Creating and Defending Against Phishing Attacks on Kali Linux

## Introduction
In this project, you will learn how to create and defend against phishing attacks using Kali Linux. Phishing is a common technique used by attackers to steal sensitive information such as usernames, passwords, and credit card details. By the end of this project, you will be able to simulate phishing attacks for educational purposes and understand how to protect against them.

## Pre-requisites
- Basic understanding of email and web technologies.
- Familiarity with using the command line interface (CLI).
- Basic knowledge of social engineering principles.

## Lab Set-up and Tools

### Diagram
Here is a simple network diagram for this lab setup:

+------------------+ +------------------+
| Attacker | | Victim |
| Kali Machine |<----->| Target Machine |
| (192.168.1.100) | | (192.168.1.101) |
+------------------+ +------------------+


### Tools
- **Kali Linux**: A Debian-derived Linux distribution designed for digital forensics and penetration testing.
- **Gophish**: An open-source phishing toolkit.
- **Email account**: For sending phishing emails.
- **Web server**: To host the phishing website (can be set up using Apache or any other web server).

### Installation
#### Gophish
1. Download the latest release of Gophish from the [official website](https://github.com/gophish/gophish/releases).
2. Extract the downloaded file:
   ```sh
   tar -xvzf gophish-vX.X.X-linux-64bit.tar.gz
   ```
3. Navigate to the extracted directory and run Gophish:
  ```
  cd gophish
  sudo ./gophish
  ```
4. Access the Gophish web interface at https://localhost:3333 (default username and password are admin and gophish).


## Tasks

### Task 1: Set Up the Phishing Campaign
- Open the Gophish web interface at https://localhost:3333.
- Create a new user group with the target email addresses.
- Create an email template for the phishing email.
- Set up a landing page to capture credentials.
- Create a new phishing campaign using the user group, email template, and landing page.

Expected Output: A configured phishing campaign ready to be launched.

### Task 2: Launch the Phishing Campaign
- In the Gophish web interface, navigate to the Email Templates section.
- Create a new email template with the following details:
-Subject: Important Update: Please Verify Your Account
  - From: support@yourcompany.com
  - Body:
    ```
    <html>
  <body>
    <h2>Dear User,</h2>
    <p>We have noticed suspicious activity on your account. Please verify your account information by clicking the link below:</p>
    <p><a href="http://192.168.1.100:8080/verify">Verify Account</a></p>
    <p>If you do not verify your account within 24 hours, your account will be locked.</p>
    <p>Thank you,<br>Your Company Support Team</p>
  </body>
  </html>
   ```
- Save the email template.
Expected Output: A phishing email template that looks convincing and prompts the user to click on a link.



### Task 3: Analyze Phishing Attack Results
- Review the data collected from the phishing campaign.
- Identify which users fell for the phishing attack and analyze the captured credentials.
Expected Output: A detailed report on the effectiveness of the phishing campaign, highlighting potential security weaknesses.

### Task 4: Defending Against Phishing Attacks
- Educate users about phishing attacks and how to recognize them.
- Implement technical measures to reduce the risk of phishing, such as:
- Enabling email filtering to block phishing emails.
- Implementing multi-factor authentication (MFA).
- Regularly updating and patching systems.
Expected Outcome: Enhanced awareness and improved defenses against phishing attacks.

Task 5: Setting Up a Phishing Awareness Program
- Develop a phishing awareness training program for employees.
- Schedule regular phishing simulation exercises using Gophish.
- Track the progress and improvement of employees over time.
Expected Outcome: Increased awareness and reduced susceptibility to phishing attacks among employees.

## Additional Resources
- Gophish Documentation
- Kali Linux Documentation
- Anti-Phishing Working Group
- Phishing Defense Guide
  
This project will help you understand how to create and defend against phishing attacks using Kali Linux and Gophish, enhancing your skills in social engineering and cybersecurity awareness.
