# 🛡️ Local Host Vulnerability Scanning Guide

## 🎯 Project Overview

This guide documents the procedure for performing a basic, unauthenticated vulnerability assessment on a local machine using **Nessus Essentials**. The process follows the required 8-step workflow to identify, analyze, and document critical system weaknesses.

---

## 🛠️ Prerequisites

* **Vulnerability Scanner:** Nessus Essentials installed and operational.
* **Target:** The local host operating system (`localhost` or local IP).

---

## 📋 Scan Execution (Steps 1–4)

This section covers the setup and execution of the vulnerability scan.

### 1. Install OpenVAS or Nessus Essentials.

* **Status:** Nessus Essentials is verified as installed and running on the host system.

### 2. Set up scan target as your local machine IP or localhost.

* **Template Selection:** Chosen the **Basic Network Scan** template for comprehensive coverage.
* **Target Configuration:** Set the target to the loopback address: `127.0.0.1` (representing `localhost`).

### 3. Start a full vulnerability scan.

* **Action:** Configuration was saved, and the scan was launched from the "My Scans" page.
* **Scan Name:** `Test_scan` (or a similar descriptive name).

### 4. Wait for scan to complete (may take 30-60 mins).

* **Monitoring:** The scan status is monitored on the "My Scans" page until it indicates **Completed**.
* **Note:** General scan time for this type of assessment is typically between 30 and 60 minutes.

---

## 🔍 Analysis and Documentation (Steps 5–8)

Once the scan is complete, the following steps are required for analysis and final reporting.

### 5. Review the report for vulnerabilities and severity.

* **Access:** Navigate to the completed scan report in the Nessus interface.
* **Review:** Examine the initial summary to note the distribution of vulnerabilities by severity (Critical, High, Medium, Low).
* **Detail:** Use the **Vulnerabilities** tab to review the individual findings.

### 6. Research simple fixes or mitigations for found vulnerabilities.

* **Guidance:** For each finding, consult the **Solution** section in the Nessus report, which recommends the specific patch, update, or configuration change needed.
* **Remediation:** Research the specific steps necessary to apply the fix to the host operating system.

### 7. Document the most critical vulnerabilities.

A formal write-up must be created, prioritizing the most severe findings. For all **Critical** and **High** severity vulnerabilities, the documentation must include:

* **Vulnerability Name:**
* **Severity:** (Critical / High)
* **Description/Impact:**
* **Recommended Solution:** (As per Nessus report)

### 8. Take screenshots of the scan results.

Visual proof of the successful execution and findings is required for the final submission.

* **Required Visuals:**
    1.  Screenshot of the "My Scans" page showing the scan as **Completed**.
    2.  Screenshot of the main **Summary** page, showing the severity bar chart breakdown.
    3.  Screenshots of the detailed view of one or more **Critical/High** findings (including the Description and Solution).
* **Reporting Alternative:** An exported PDF or HTML report from Nessus can be used to supplement or replace simple screenshots.

---
