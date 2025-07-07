# Windows and Apache Log Analysis (Project 3)

**Author**: Andrew Boschini  
**Role**: Security Analyst  
**Certifications in Progress**: Security+, Splunk Core Certified Power User  
**Tools Used**: Splunk, Apache, Windows Event Viewer

---

## Overview

This project simulates a real-world security operations task for Virtual Space Industries (VSI), where intelligence suggested a targeted cyberattack by a rival company, JobeCorp. Logs from a Windows server and Apache web server were analyzed using Splunk to identify the attack timeline, visualize suspicious behavior, and configure detection alerts and dashboards.

---

## Objectives

- Ingest and normalize Windows and Apache logs using Splunk
- Establish behavioral baselines
- Detect indicators of compromise and attack progression
- Configure detection alerts and visual dashboards
- Recommend future mitigations based on findings

---

## Logs Analyzed

- **Windows Server Logs**: Event IDs related to logons, account deletion, privilege escalation, system changes, and audit clears.
- **Apache Web Server Logs**: HTTP methods (GET/POST), response codes, IP origins, referrer domains, and URI paths.

---

## Key Findings

### Windows Activity
- Spikes in **Event ID 4624** (successful logons) and **Event ID 4672** (privilege assignments)
- Frequent **account deletions** (Event ID 4726) and **audit log clears**
- High logon counts from `user_a` and `user_k` suggesting credential compromise
- Signature trends indicated repeated access to sensitive operations

### Apache Activity
- POST request spike up to 1,415 requests/hour
- Suspicious targeting of `/VSI_Account_logon.php`
- High 404/500 error rates indicating probing and misconfigurations
- Foreign IPs (notably from Ukraine) triggered geographic traffic spike alerts
- Semicomplete.com as a top referrer in suspicious sessions

---

## Reports and Alerts

### Windows
- **Reports**: Failed Logons, Signature Trends, Severity Breakdown
- **Alerts**:
  - Excessive Successful Logons (>40/hr)
  - Excessive User Deletions (>5/hr)
  - Failed Logon Spike (>20/hr)

### Apache
- **Reports**: HTTP Method Count, Response Code Count, Top Referrers
- **Alerts**:
  - Foreign Traffic Spike (>100/hr from non-US IPs)
  - POST Method Spike (>50/hr)

---

## Dashboards

- **Windows Monitoring**: Event frequency by type, logon anomalies, user activity trends
- **Apache Monitoring**: HTTP methods over time, top URIs, geographic traffic maps, referrer domain charts

---

## Mitigations

- Enable multi-factor authentication (MFA) for all administrative accounts
- Implement geofencing on external-facing applications
- Rate-limit HTTP POST requests on sensitive endpoints
- Deploy automated alerting and response workflows
- Regularly tune alert thresholds to reflect evolving baselines

---

## Files Included

- `project3-presentation.pdf` – Full attack timeline, dashboards, alerts, and recommendations
- `review-summary.md` – Optional summary of attack findings and alert effectiveness
