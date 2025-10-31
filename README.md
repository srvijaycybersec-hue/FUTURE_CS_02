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
index=soc_index sourcetype="network_logs" dest_port=4444

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
