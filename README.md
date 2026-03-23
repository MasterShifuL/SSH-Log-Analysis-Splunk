# 🛡️ SSH Log Analysis using Splunk

## 📌 Objective
This project focuses on analyzing SSH authentication logs using Splunk to detect suspicious activities such as brute-force attacks, failed logins, and unauthorized access attempts.

The main objectives include:
- Identifying successful and failed SSH login attempts  
- Detecting brute-force attack patterns  
- Monitoring suspicious unauthenticated connections  
- Building dashboards and alerts for security monitoring  

---

## 🧠 Skills Learned
- Log analysis using Splunk (SIEM)
- Detecting brute-force attacks from logs
- Writing SPL (Search Processing Language)
- Data visualization (charts & dashboards)
- Alert configuration in Splunk
- Understanding SSH authentication behavior

---

## 🛠️ Tools Used
- Splunk Enterprise / Splunk Free
- SSH log dataset (JSON format)
- Ubuntu / Linux environment

---

## 🚀 Steps

---

### 🔹 Task 1: Ingest and Parse Logs

Upload SSH logs into Splunk and verify field extraction.

#### 🔍 Query:
```spl
index=ssh_logs | stats count by event_type
