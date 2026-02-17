# SOC Investigation Case Study — Blacklisted URL Firewall Alert (Splunk SIEM)

## Overview
This project documents a SOC-style investigation performed in a simulated environment using a SIEM (Splunk) and firewall alert dashboard.  
The alert involved an internal host attempting to access a blacklisted shortened URL. The connection was successfully blocked by firewall controls.

The objective was to validate the alert, pivot in SIEM logs, determine impact, and produce an incident report.

---

##  Tools Used
- Splunk SIEM (Search & Reporting)
- Firewall log datasource
- SOC alert dashboard
- Indicator pivoting (IP + URL search)

---

## Alert Summary
- **Alert Type:** Access to Blacklisted External URL
- **Severity:** High
- **Source:** Firewall
- **Action:** Blocked
- **Technique Pattern:** Suspicious shortened URL (bit.ly)
- **Initial Risk:** Possible phishing or malicious redirect attempt

---

##  Investigation Steps

1. Opened alert in SOC dashboard
2. Collected key indicators:
   - Source IP
   - Destination IP
   - URL
   - Timestamp
3. Pivoted to Splunk SIEM
4. Expanded time window to include alert timeframe
5. Searched by source IP
6. Confirmed firewall blocked event in logs
7. Reviewed surrounding web activity for user context
8. Pivot searched destination IP and URL domain
9. Correlated activity timeline
10. Determined alert classification

---
## Sample Splunk Queries Used

10.20.2.17
67.199.248.11
bit.ly

Field-based searches:src_ip=10.20.2.17
dest_ip=67.199.248.11
url="bit.ly"


---

## Key Findings

- Internal host attempted outbound connection to blacklisted shortened URL
- Firewall policy blocked the connection
- SIEM logs confirmed the alert event
- URL shorteners are commonly used in phishing campaigns
- Related browsing activity suggests possible phishing lure interaction
- No successful connection observed

---

##  Classification

**True Positive — Prevented**

The alert corresponds to real blocked malicious/suspicious activity confirmed in SIEM logs.

---

## Escalation Decision

**Escalated:** Yes

Reason:
Even though blocked, access attempt to blacklisted URL indicates user or endpoint risk and requires follow-up review.

---

## Recommended Remediation Actions

- Review endpoint activity for source host
- Check related email and browsing logs
- Run endpoint security scan
- Provide user awareness guidance
- Monitor for repeat attempts

---

##  Indicators of Interest (IOCs)

- Source IP: `10.20.2.17`
- Destination IP: `67.199.248.11`
- URL: `bit.ly/3sHkX3da12340`
- Firewall Rule: Blocked Websites

---

##  Skills Demonstrated

- SIEM log analysis
- SOC alert triage
- Indicator pivoting
- Firewall event validation
- Incident classification
- Case report writing
- Investigation workflow

---

##  Notes

This investigation was performed in a controlled training environment.  
All data is simulated and used for educational SOC analyst practice.


##  Sample Splunk Queries Used
