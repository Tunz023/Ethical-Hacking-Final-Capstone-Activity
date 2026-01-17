# 🛡️ Ethical Hacking Final Capstone Activity  
**Instructor-Led Capture The Flag (CTF) Exercise**  
**By Motunrayo Lawal**

---

## 📌 Overview

This repository documents my Final Capstone Ethical Hacking Assessment, an instructor-led capture-the-flag style exercise.

The objective was to simulate real-world penetration testing by identifying vulnerabilities, exploiting them ethically, retrieving flag files, and recommending remediation steps.

All activities were conducted in a controlled lab environment for educational purposes only.

---

## ⚠️ Ethical Disclaimer

This project was completed strictly for learning and ethical hacking purposes:
- Performed in a private lab environment
- Targeted intentionally vulnerable systems
- No production or unauthorized systems were tested

---

## 🎯 Objectives

- Perform reconnaissance and vulnerability identification  
- Exploit discovered vulnerabilities ethically  
- Retrieve flag files from compromised systems  
- Recommend remediation measures to reduce risk  

---

## 🧪 Lab Environment

- **Attacker Machine:** Kali Linux  
- **Target Networks:**  
  - 10.5.5.0/24  
  - 192.168.0.0/24  
- **Web Application:** Damn Vulnerable Web Application (DVWA)  

---

## 🧩 Challenges Completed

---

### 🔹 Challenge 1: Use SQL injection to find a flag file.

**Backgroun/Scenario:**  
You have been hired to conduct a penetration test for a customer. At the conclusion of the test, the customer has requested a complete report that includes any vulnerabilities discovered, successful exploits, and remediation steps to protect vulnerable systems. You have access to hosts on the 10.5.5.0 and 192.168.0.0/24 networks.

#### Steps Performed
1. Accessed DVWA at `10.5.5.12`
2. Logged in using default credentials (`admin / password`)
3. Set DVWA security level to **Low**
4. Identified vulnerable input fields
5. Executed SQL Injection payloads
6. Extracted database information
7. Retrieved user credentials
8. Cracked the password hash
9. Logged into `192.168.0.10` as Bob Smith
10. Retrieved the flag file

#### Key Findings
- **Flag File:** `mypasswords.txt`
- **Flag Code:** `8748wf8J`

#### Why This Matters
SQL Injection allows attackers to bypass authentication, extract sensitive data, and compromise entire databases if input validation is weak.

#### Remediation Recommendations
- Use parameterized queries
- Implement strict input validation
- Apply least-privilege database access
- Hide detailed error messages
- Conduct regular security testing

---

### 🔹 Challenge 2: Web Server Vulnerabilities 

**Goal:**  
In this part, you must find vulnerabilities on an HTTP server. Misconfiguration of a web server can allow for the listing of files contained in directories on the server. You can use any of the tools you learned in earlier labs to perform reconnaissance to find the vulnerable directories.
In this challenge, you will locate the flag file in a vulnerable directory on a web server.


#### Steps Performed
1. Performed reconnaissance on the web server
2. Identified directories with indexing enabled
3. Accessed exposed directories
4. Retrieved the flag file

#### Vulnerable Directories
- `/config/`
- `/external/`

#### Key Findings
- **Flag File:** `db_form.html`
- **Directory:** `/config/`
- **Flag Code:** `aWe-4975`

#### Why This Matters
Directory listing can expose sensitive files, internal structure, and configuration data.

#### Remediation Recommendations
- Disable directory indexing
- Apply proper file and directory permissions

---

### 🔹 Challenge 3: Exploit open SMB Server Shares

**Goal:**  
In this part, you want to discover if there are any unsecured shared directories located on an SMB server in the 10.5.5.0/24 network. You can use any of the tools you learned in earlier labs to find the drive shares available on the servers.

#### Steps Performed
1. Scanned the network for SMB services
2. Identified a host running SMB
3. Enumerated accessible SMB shares
4. Accessed shares anonymously
5. Retrieved the flag file

#### Target Identified
- **SMB Host:** `10.5.5.14`

#### Accessible Shares
- `workfiles`
- `print$`
- `IPC$`

#### Key Findings
- **Share:** `print$`
- **Flag File:** `sxij42.txt`
- **Flag Code:** `NWs39691`

#### Why This Matters
Open SMB shares can lead to data leakage, lateral movement, and network compromise.

#### Remediation Recommendations
- Disable anonymous SMB access
- Restrict SMB using firewalls and access controls

---

### 🔹 Challenge 4: Analyze a .pcap file to find information.

**Goal:**  
As part of your reconnaissance effort, your team captured traffic using Wireshark. The capture file, SA.pcap, is located in the Downloads subdirectory within the kali user home directory.

#### Steps Performed
1. Opened `SA.pcap` using Wireshark
2. Analyzed HTTP traffic
3. Identified exposed directories and files
4. Retrieved flag data

#### Key Findings
- **Target IP:** `10.5.5.11`
- **Exposed Directories:**  
  `/test/`, `/data/`, `/includes/`, `/passwords/`, `/styles/`, `/javascript/`, `/webservices/`
- **Flag File URL:**  
  `http://10.5.5.11/data/user_accounts.xml`
- **Flag Code:** `21z-1478K`

#### Why This Matters
Unencrypted traffic allows attackers to intercept sensitive information.

#### Remediation Recommendations
- Enforce HTTPS with TLS
- Disable directory browsing
- Encrypt sensitive data in transit

---

## 📌 Key Takeaways

- Small misconfigurations can lead to serious breaches
- Input validation and access control are critical
- Ethical hacking requires proper documentation
- Continuous testing improves security posture

---

