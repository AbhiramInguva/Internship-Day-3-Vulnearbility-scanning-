# 🔒 Cybersecurity Foundations Project: Firewall Management & Vulnerability Assessment

This project repository documents two core cybersecurity exercises: hands-on firewall rule management and theoretical knowledge of vulnerability assessment and management principles.

## 1. 🛡️ Firewall Rule Management Exercise Documentation

This section provides the necessary commands and procedures to complete a basic firewall rule management exercise using Windows Firewall or Linux (UFW).

### 1.1. Exercise Objectives

The goal is to practice listing, adding, testing, and removing firewall rules to control inbound traffic.

| Step | Windows Firewall (PowerShell) | Linux (UFW) |
| :--- | :--- | :--- |
| **1. Open Tool** | `Get-NetFirewallRule -Direction Inbound` (To confirm tool access) | `sudo ufw status` |
| **2. List Rules** | `Get-NetFirewallRule -Direction Inbound` | `sudo ufw status verbose` |
| **3. Add Block Rule**| `New-NetFirewallRule -DisplayName "Block Telnet 23" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block` | `sudo ufw deny 23/tcp comment 'Block Telnet 23'` |
| **4. Test Rule** | **(See Section 1.2)** | **(See Section 1.2)** |
| **5. Allow SSH (Linux Only)** | N/A | `sudo ufw allow 22/tcp comment 'Allow SSH'` |
| **6. Remove Block Rule**| `Remove-NetFirewallRule -DisplayName "Block Telnet 23"` | `sudo ufw delete deny 23/tcp` |
| **7. Document Steps**| Document the PowerShell or GUI steps used. | Document the exact commands used. |
| **8. Summarize Filtering**| A firewall filters traffic by inspecting network packet headers (IP, Port, Protocol) against ordered rules (policy), often using stateful inspection to track active connections.  | |

### 1.2. Rule Testing (Step 4)

The test is successful if the connection attempt fails, indicating the firewall blocked the traffic.

| Tool | Command Example (Testing port 23 on the local machine) | Expected Success Output |
| :--- | :--- | :--- |
| **Windows (PowerShell)** | `Test-NetConnection -Port 23 -ComputerName localhost` | Output shows `TcpTestSucceeded : False` or times out. |
| **Linux (Netcat)** | `nc -vz 127.0.0.1 23` | Output shows "Connection refused" or a timeout. |

---

## 2. 🧠 Vulnerability Management Fundamentals

This section answers foundational questions on vulnerability assessment and management, based on industry best practices and common security reporting.

### 2.1. What is Vulnerability Scanning?

Vulnerability scanning is an automated process of inspecting systems (networks, applications, and operating systems) against a database of **known security weaknesses** (CVEs). It produces a report detailing potential flaws to guide patching and remediation efforts.

### 2.2. Difference Between Vulnerability Scanning and Penetration Testing

| Feature | Vulnerability Scanning | Penetration Testing (Pen Testing) |
| :--- | :--- | :--- |
| **Goal** | Identify **known** weaknesses and inventory vulnerable assets. | Exploit identified vulnerabilities to assess **real-world impact** and system defense. |
| **Methodology**| Automated, tool-driven, high-speed, and non-intrusive. | Manual, hands-on, highly intrusive, and goal-oriented. |

### 2.3. Common Vulnerabilities in Personal Computers

Common risks on personal machines often include:
* **Outdated Software:** Operating systems and applications with unpatched security flaws.
* **Weak Passwords:** Easily guessable or reused credentials.
* **Misconfigured Firewalls:** Default or incorrectly configured network security settings.

### 2.4. How Do Scanners Detect Vulnerabilities?

Scanners typically follow this process:

1.  **Host Discovery:** Identifying active devices on the network.
2.  **Service Fingerprinting:** Determining the exact version and configuration of running services (e.g., Apache HTTP Server version).
3.  **Vulnerability Checks:** Comparing discovered versions/configurations against a database of known security flaws.
4.  **Reporting:** Compiling results categorized by severity.

### 2.5. What is CVSS?

**CVSS** stands for **Common Vulnerability Scoring System**. It is an open, standardized method used to numerically rate the severity of software vulnerabilities on a scale from 0.0 (low) to 10.0 (high). 

### 2.6. How Often Should Vulnerability Scans Be Performed?

Scan frequency should be based on risk and compliance requirements:
* **External/Internet-Facing Assets:** Weekly or Bi-weekly.
* **Internal Network Assets:** Monthly.
* **Critical Systems:** Quarterly (minimum compliance requirement).

### 2.7. What is a False Positive in Vulnerability Scanning?

A **false positive** occurs when the scanner flags a weakness that does not actually exist or is not exploitable in the target system's context. This often happens if the scanner detects a vulnerable version number but fails to recognize that a security patch has been backported by the vendor.

### 2.8. How Do You Prioritize Vulnerabilities?

Prioritization should focus on **Risk**, combining severity with asset context and exploitability. 

1.  **Exploitability and Severity (HIGH Priority):** Address vulnerabilities with a high CVSS/VPR score *and* a known, active exploit in the wild.
2.  **Asset Criticality:** Prioritize flaws on critical business assets (e.g., core databases, primary web servers).
3.  **Mitigation Availability:** Fix simple configuration flaws or vulnerabilities with readily available, tested patches first.
