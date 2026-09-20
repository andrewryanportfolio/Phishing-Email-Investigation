# Phishing Email Investigation

### SOC Analyst Portfolio | Simulated Security Investigation

## Project Overview

This project documents my investigation of a simulated credential-phishing email from the perspective of a Level 1 SOC Analyst.

The objective was to examine suspicious email indicators, understand authentication results, assess the potential threat and recommend appropriate incident-response actions.

**Disclaimer:** This project uses fictional email data and hypothetical authentication results. No real malicious website was visited or company information was used.

---

## Investigation Summary

An employee reported receiving an email claiming to be from IT Support.

The email warned that their Microsoft 365 account would be suspended unless they verified their credentials within 24 hours.

I investigated the sender address, message content, suspicious URL and simulated email authentication results.

### Key findings

| Indicator          | Finding                                      |
| ------------------ | -------------------------------------------- |
| Sender domain      | Different from the legitimate company domain |
| Social engineering | Urgency and threat of account suspension     |
| Suspicious URL     | Unexpected password-reset link               |
| SPF                | Pass for a non-aligned domain                |
| DKIM               | Fail                                         |
| DMARC              | Fail                                         |

**Final classification: Suspected Credential Phishing**

The indicators support treating the message as suspicious, but credential theft was not confirmed.

---

## Investigation Methodology

I followed five investigation stages:

1. **Sender analysis:** Compared the sender address with the legitimate organisation's domain.
2. **Content analysis:** Identified urgency and fear tactics.
3. **URL analysis:** Examined the hostname and path without visiting the destination.
4. **Email authentication:** Interpreted simulated SPF, DKIM and DMARC results.
5. **Incident response:** Determined appropriate actions to protect the user and escalate the incident.

---

## Skills Demonstrated

* Email security fundamentals
* Phishing identification
* Social engineering analysis
* URL structure analysis
* SPF, DKIM and DMARC interpretation
* Incident classification
* Incident-response recommendations
* Technical documentation

---

## Project Files

### [Full Investigation Report](investigation-report.md)

The complete investigation, including technical findings, classification, recommended response actions and lessons learned.

### [Simulated Phishing Email](sample-phishing-email.txt)

The fictional email used as evidence for this investigation.

---

## Recommended Incident Response

My recommended actions were to:

* Warn the employee not to click the suspicious link or enter credentials.
* Escalate the email using the organisation's security reporting procedure.
* Investigate whether other employees received similar messages.
* Determine whether the employee clicked the link or submitted credentials.
* Consider validated indicators for blocking or monitoring in accordance with organisational procedures.

These are recommended actions for a simulated scenario. No live incident-response actions were performed.

---

## Lessons Learned

This project improved my understanding of phishing investigations and email authentication.

I learned that an SPF pass does not automatically establish that the visible sender is legitimate.

I also learned that DKIM failure does not necessarily prove email tampering and that DMARC depends on aligned authentication.

Most importantly, I learned to distinguish observable evidence from assumptions when classifying a potential security incident.

---

## Future Improvements

* Analyse a real, safely sanitised phishing email.
* Practise extracting and interpreting genuine email headers.
* Use authorised security tools to analyse publicly shareable indicators.
* Investigate related activity using SIEM logs in a controlled lab.

---

**Project status:** Completed simulated investigation.
