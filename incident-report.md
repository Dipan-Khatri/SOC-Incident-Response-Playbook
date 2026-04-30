# 🚨 Incident Response Report – Brute Force Login Attempt

---

## 📅 Incident Summary

* **Date Detected:** April 29, 2026
* **Alert Name:** Brute Force Login Detection
* **Severity:** Medium
* **Detection Tool:** Splunk SIEM

---

## 🔍 What Happened?

A scheduled alert in Splunk was triggered due to multiple failed login attempts originating from a single IP address.

* **Suspicious IP:** 192.168.1.10
* **Failed Attempts:** 5+ within a short time window

This behavior is consistent with a **brute-force attack**, where an attacker repeatedly attempts different password combinations to gain unauthorized access.

---

## ⚠️ Why This Is Suspicious

* High number of failed login attempts from a single IP
* Rapid repeated activity indicating possible automation
* Targeting a privileged account: **admin**

These indicators strongly suggest an **unauthorized access attempt**.

---

## 🧪 Investigation Steps (SOC Workflow)

1. Reviewed alert in Splunk (Triggered Alerts section)
2. Validated detection query results
3. Identified IP with abnormal activity
4. Analyzed login activity timeline
5. Checked targeted user accounts
6. Confirmed repeated FAILED login status

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

### 🔔 Triggered Alert

![Triggered Alert](PASTE_ALERT_IMAGE_LINK)

### 🧪 Detection Result

![Detection Result](PASTE_QUERY_IMAGE_LINK)

---

## 🧾 Sample Log Format

```
2026-04-23 10:01:00, 192.168.1.10, admin, FAILED
2026-04-23 10:01:05, 192.168.1.10, admin, FAILED
2026-04-23 10:01:10, 192.168.1.10, admin, FAILED
```

---

## 🧯 Response Actions (Simulated)

If this were a real SOC environment:

* 🚫 Block the suspicious IP address at firewall level
* 🔐 Temporarily lock the targeted user account
* 📢 Notify security team and escalate if needed
* 📊 Monitor logs for continued or related activity

---

## 🧠 SOC Thinking Applied

* Identified abnormal authentication behavior
* Correlated repeated failures to a single IP
* Recognized brute-force attack pattern
* Proposed containment and mitigation actions

---

## 📚 Lessons Learned

* Detection thresholds must be carefully tuned
* Early alerting helps prevent account compromise
* Log analysis provides clear visibility into attack patterns

---

## 💡 Key Insight

Even simple log data can reveal clear attack patterns when analyzed correctly.
A single IP with repeated failed login attempts is a strong indicator of a brute-force attack.

---

## 🎯 Conclusion

The alert successfully identified suspicious login activity.
This simulation demonstrates how SOC analysts detect, investigate, and respond to brute-force attacks using SIEM tools like Splunk.

---
