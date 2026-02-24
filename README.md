# Sentinel-Hunts
Sentinel-Hunts. Persistence - Execution - Initial Access
Microsoft Sentinel Threat Hunting Library (KQL)
This repository contains advanced Kusto Query Language (KQL) hunts for Microsoft Sentinel. These queries are designed to bridge the gap between standard alerts and proactive hunting, focusing on Entra ID (Azure AD), Office 365, and Windows Security Events.

Gemini said
Here is a clean, high-impact README.md specifically for your Sentinel folder. It’s designed to show that you understand KQL (Kusto Query Language) and cloud-native security.

🛡️ Microsoft Sentinel Threat Hunting Library (KQL)
This repository contains advanced Kusto Query Language (KQL) hunts for Microsoft Sentinel. These queries are designed to bridge the gap between standard alerts and proactive hunting, focusing on Entra ID (Azure AD), Office 365, and Windows Security Events.

📊 MITRE ATT&CK® Cloud & Endpoint Mapping
Tactic	Focus Area	Primary KQL Table	Technique
Initial Access	Password Spraying / Brute Force	SigninLogs	T1110
Execution	Encoded PowerShell Payloads	SecurityEvent	T1059.001
Persistence	Privileged Role Escalation	AuditLogs	T1098
Exfiltration	Anomalous Data Transfers	OfficeActivity	T1048

📂 Featured Hunts
1. Brute Force Breakthrough Detection
Goal: Identify successful logins that were preceded by multiple failures from the same IP.

Scenario: An attacker spends hours brute-forcing a password and finally gains access. Standard logs show individual failures, but this query connects the dots.

Query: SigninLogs_BruteForce_Success.kql

2. Privileged Role Monitoring (Shadow Admin)
Goal: Detect when a user is added to high-impact roles like Global Administrator.

Scenario: Monitoring for "Identity-based" persistence. If an attacker compromises a helpdesk account, they may try to promote themselves to full admin.

Query: Audit_Privileged_Role_Add.kql

3. Suspicious PowerShell Encoding
Goal: Uncover "Hidden" execution strings used in fileless malware.

Scenario: Flagging the use of -enc or -EncodedCommand flags which are often used to bypass basic command-line logging.

Query: SecurityEvent_Encoded_PowerShell.kql

🛠️ How to Use
Open Microsoft Sentinel: Navigate to the Logs or Hunting blade.

Paste & Run: Copy the .kql files from this directory into the query editor.

Time Ranges: Ensure you set the time picker to Last 24 Hours or Last 7 Days for best results.

Baseline: Customize the where clauses to exclude your known-safe service accounts or internal IP ranges.

