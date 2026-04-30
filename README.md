# SOC-Incident-Response-Playbook-

# 🚨 Incident Response Report – Brute Force Login Attempt

## 📅 Incident Summary

* **Date Detected:** April 29, 2026
* **Alert Name:** Brute Force Login Detection
* **Severity:** Medium
* **Detection Tool:** Splunk SIEM

---

## 🔍 What Happened?

A scheduled alert in Splunk triggered due to multiple failed login attempts from a single IP address.

* Suspicious IP: **192.168.1.10**
* Failed Attempts: **5+ within short time window**

This behavior is consistent with a **brute-force attack**, where an attacker repeatedly tries different passwords.

---

## ⚠️ Why This Is Suspicious

* High number of failed login attempts
* Rapid repeated activity (possible automation)
* Targeting privileged account: **admin**

---

## 🧪 Investigation Steps (SOC Workflow)

1. Checked Splunk alert (Triggered Alerts section)
2. Verified detection query results
3. Identified IP with abnormal activity
4. Analyzed login timeline
5. Reviewed targeted usernames
6. Confirmed repeated FAILED status

---

## 🛠 Detection Query Used

```
index=* FAILED
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| stats count by ip
| where count > 3
```

---

## 🧾 Evidence

* Alert triggered in Splunk
* IP with repeated failed attempts
* Log patterns showing brute-force behavior

(Screenshots included in repository)

---

## 🧯 Response Actions (Simulated)

* 🚫 Block suspicious IP address
* 🔐 Lock affected account temporarily
* 📢 Notify security team
* 📊 Monitor for further activity

---

## 🧠 Lessons Learned

* Detection thresholds are critical
* Early alerts help prevent compromise
* Log analysis reveals attack patterns

---

## 🎯 Conclusion

The alert successfully detected suspicious login behavior.
This simulation demonstrates how SOC analysts investigate and respond to brute-force attacks.

---
