# 🛡️ SSH Log Analysis using Splunk

---

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
````

#### 📸 Screenshots:

**1. Upload Data Screen**

```md
![Ref 1.1 - Upload Data](screenshots/ref1_upload.png)
```

**2. Sourcetype Configuration (_json)**

```md
![Ref 1.2 - Sourcetype](screenshots/ref1_sourcetype.png)
```

**3. Index Creation (ssh_logs)**

```md
![Ref 1.3 - Index](screenshots/ref1_index.png)
```

**4. Validation Search Result**

```md
![Ref 1.4 - Validation Query](screenshots/ref1_validation.png)
```

📝 *Ref 1: SSH log successfully ingested and parsed in Splunk*

---

### 🔹 Task 2: Analyze Failed Login Attempts

Identify IP addresses that generate failed login attempts.

#### 🔍 Query:

```spl
index=ssh_logs event_type="Failed SSH Login"
| stats count by id.orig_h
| sort -count
| head 10
```

#### 📸 Screenshots:

**1. Search Query Result**

```md
![Ref 2.1 - Failed Login Result](screenshots/ref2_result.png)
```

**2. Bar Chart Visualization**

```md
![Ref 2.2 - Bar Chart](screenshots/ref2_barchart.png)
```

📝 *Ref 2: Top source IPs generating failed SSH login attempts*

---

### 🔹 Task 3: Detect Brute Force Attempts

Detect multiple failed authentication attempts.

#### 🔍 Query:

```spl
index=ssh_logs event_type="Multiple Failed Authentication Attempts"
| stats count by id.orig_h, id.resp_h
```

#### 📸 Screenshots:

**1. Search Result**

```md
![Ref 3.1 - Brute Force Result](screenshots/ref3_result.png)
```

**2. Alert Configuration Page**

```md
![Ref 3.3 - Alert Setup](screenshots/ref3_alert.png)
```

📝 *Ref 3: Detection of brute-force attack patterns and alert setup*

---

### 🔹 Task 4: Track Successful Logins

Analyze successful SSH login activity.

#### 🔍 Query:

```spl
index=ssh_logs event_type="Successful SSH Login"
| stats count by id.orig_h, id.resp_h
```

#### 📸 Screenshots:

**1. Search Result**

```md
![Ref 4.1 - Successful Login](screenshots/ref4_result.png)
```

**2. Dashboard Panel**

```md
![Ref 4.2 - Dashboard Panel](screenshots/ref4_dashboard.png)
```

📝 *Ref 4: Monitoring successful SSH login activity*

---

### 🔹 Task 5: Detect Suspicious Unauthenticated Connections

Identify connections without authentication.

#### 🔍 Query:

```spl
index=ssh_logs event_type="Connection Without Authentication"
| stats count by id.orig_h
```

#### 🔍 Timechart:

```spl
index=ssh_logs event_type="Connection Without Authentication"
| timechart count by id.orig_h
```

#### 📸 Screenshots:

**1. Search Result**

```md
![Ref 5.1 - Unauthenticated Result](screenshots/ref5_result.png)
```

**2. Timechart Visualization**

```md
![Ref 5.2 - Timechart](screenshots/ref5_timechart.png)
```

📝 *Ref 5: Detection of suspicious SSH connections without authentication*

---

## 📊 Dashboard

Create a dashboard combining:

* Failed login attempts
* Successful logins
* Brute-force detection
* Unauthenticated connections

#### 📸 Screenshots:

```md
![Ref 6 - Full Dashboard](screenshots/ref6_dashboard.png)
```

📝 *Ref 6: Security monitoring dashboard for SSH activity*

---


## 🧾 Conclusion

This project demonstrates how Splunk can be used as a SIEM tool to monitor and analyze SSH logs effectively.

### Key Achievements:

* Detected brute-force attacks
* Identified suspicious login patterns
* Built real-time monitoring dashboards
* Configured alerts for security threats

This project reflects practical SOC Analyst skills and strengthens cybersecurity portfolio readiness.

---
