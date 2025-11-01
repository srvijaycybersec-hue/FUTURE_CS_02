# 🛡️ FUTURE_CS_02 — Security Alert Monitoring & Incident Response

## 📌 Objective
The goal of this project is to **monitor security alerts**, **analyze suspicious activities**, and **draft incident response actions** to help organizations stay secure against cyber threats.

---

## 👤 Intern Details

| **Field** | **Details** |
|------------|-------------|
| **Name** | Vijay S R |
| **Role** | Cybersecurity Intern |
| **Program** | Future Interns — Cybersecurity Internship |
| **Task** | Security Alert Monitoring & Incident Response |

---

## ✅ Tasks Performed

1. **Set up a SIEM Tool**  
   - Installed and configured **Splunk Enterprise (Free Trial)** for log ingestion and analysis.

2. **Prepared & Uploaded Logs**  
   - Created and uploaded simulated logs:  
     `auth.log`, `network.log`, `malware.log`, `firewall.log`

3. **Analyzed Security Alerts**  
   - Used **SPL (Search Processing Language)** queries to detect anomalies and suspicious activities.

4. **Classified Incidents**  
   - Categorized alerts by **severity levels**: *High, Medium, Low*.

5. **Created Visual Dashboards**  
   - Built Splunk dashboards to visualize alerts, frequency, and patterns.

6. **Drafted Incident Response Report**  
   - Documented incident details including **evidence**, **impact**, and **remediation recommendations**.

---

## 🛠️ Tools Used

| **Tool / Resource** | **Purpose** |
|----------------------|-------------|
| **Splunk Enterprise (Free Trial)** | SIEM for log ingestion, correlation, and visualization |
| **Sample Log Files** | Simulated log sources (auth, network, malware, firewall) |
| **Google Docs / MS Word** | Drafting the incident response report |

---

## 📁 Log Files Overview

| **Log File** | **Description** |
|---------------|-----------------|
| `auth.log` | Authentication attempts (login success/failure) |
| `network.log` | Network connections (source/destination IPs, ports) |
| `malware.log` | Malware detection alerts (type, severity) |
| `firewall.log` | Firewall actions (allowed/blocked connections) |

---

## 🔍 Example SPL Queries


# Filter by Source Type
index=soc_index sourcetype="auth.logs"

# Find failed logins
index=soc_index sourcetype="auth.logs" status=failed

# Brute force attempts from same IP
index=soc_index sourcetype="auth.logs" status=failed | stats count by user, ip | where count >= 3

# Filter for unusual ports
index=* source="network.log" sourcetype="network_logs" DPT=3389 | stats count by DST

# High & Critical malware alerts
index=soc_index sourcetype="malware_logs" severity=High OR severity=Critical

# Blocked connections by source IP
index=soc_index sourcetype="firewall_logs" action=Blocked

# External authentication attempts
index=soc_index sourcetype="auth.logs" | search NOT ip="192.168.*"

# Frequent firewall blocks
index=soc_index sourcetype="firewall_logs" action=Blocked | stats count by src_ip | sort - count

# Failed logins by user
index=soc_index sourcetype="auth.logs" status=failed | stats count by user

# Failed malware remediation
index=soc_index sourcetype="malware_logs" status=Failed

# Unusual network ports
index=soc_index sourcetype="network_logs" NOT dest_port=22 NOT dest_port=80 NOT dest_port=443

Classify Alerts

• IP, user, host • Description (e.g., brute force, malware) • Priority (High, Medium, Low)

Incident ID Description Source Type Host/IP Priority Action INC001 Multiple failed logins auth.logs 203.0.113.5 High Block IP, reset password INC002 Ransomware detected malware_logs PC-45 Critical Isolate, clean, patch INC003 Suspicious port used network_logs 192.168.1.20 Medium Investigate
🚩 How to Run This Project

Install Splunk (free trial) locally or on a VM.

Upload sample log files via Settings > Add Data > Upload.

Create an index, e.g., soc_index.

Use Search & Reporting to test your SPL queries.

Save searches as Dashboard Panels to visualize results.

Monitor and analyze alerts from the dashboard.
Future Enhancements
• Automate log ingestion using forwarders.
• Add real-time alert notifications with emails or Slack integration.
• Integrate threat intelligence feeds to correlate IOCs.
• Implement playbooks for automated incident response actions.
• Improve dashboards with geo-location mapping and advanced visualizations.
• Expand to additional log sources (Windows Event Logs, Cloud Logs)
