# Phishing Email Investigation Report

**Analyst:** Andrew Ryan

**Project:** SOC Analyst Portfolio

**Case Type:** Simulated Credential Phishing

**Classification:** Suspected Credential Phishing

**Status:** Investigation documented: simulated case

---

## 1. Investigation Overview

This project documents my investigation of a simulated phishing email from the perspective of a Level 1 SOC Analyst.

The purpose of this investigation was to identify suspicious indicators, analyse email authentication results, assess the potential threat and recommend appropriate response actions.

This investigation uses fictional email data and hypothetical authentication results. No real malicious URL was visited, and no company systems or confidential information were used.

## 2. Initial Incident

An employee reported receiving an email claiming to be from the IT Support team.

The email stated that their Microsoft 365 account would be suspended unless they verified their credentials within 24 hours.

The email contained a link directing the employee to an unverified password-reset page.

**Email details:**

* Display name: IT Support
* Sender: [helpdesk@company-support.example](mailto:helpdesk@company-support.example)
* Recipient: [employee@company.example](mailto:employee@company.example)
* Subject: URGENT: Your Account Will Be Disabled
* URL: hxxps://login-security.example/reset

All domains and addresses in this report are fictional.

---

## 3. Investigation Findings

### Finding 1: Sender Domain Analysis

I examined the sender's email address and compared it with the legitimate organisation's domain.

Sender domain: `company-support.example`

Legitimate company domain: `company.example`

I identified that the domains did not match.

Although a domain mismatch does not automatically prove an email is malicious, it raises suspicion and requires further investigation.

### Finding 2: Social Engineering

I analysed the email body and identified urgency and fear as the main social engineering techniques.

The email claimed that the employee's Microsoft 365 account would be suspended unless they verified their credentials within 24 hours.

The message attempted to pressure the recipient into taking immediate action by following a link.

I considered this suspicious because it combined an unexpected request for credentials with a threat of account suspension.

### Finding 3: URL Analysis

I examined the URL provided in the email:

`hxxps://login-security.example/reset`

I identified the following components:

* Scheme (defanged): hxxps
* Hostname: login-security.example
* Path: /reset

The hostname differs from the legitimate organisation's domain.

Combined with the email's request for urgent credential verification, this raises suspicion of credential phishing.

I did not visit the URL or verify its actual behaviour. Therefore, I cannot confirm that the destination hosts a credential-harvesting website.

---

## 4. Email Authentication Analysis

I examined the hypothetical authentication results provided in the training scenario.

| Authentication | Result |
| -------------- | ------ |
| SPF            | PASS   |
| DKIM           | FAIL   |
| DMARC          | FAIL   |

**SPF Analysis**

SPF passed for the envelope sender domain `mailer.example`.

This indicates that the sending IP was authorised for the SPF-checked domain in the simulated results.

However, the authenticated domain did not align with the visible From domain, `company-support.example`.

Therefore, the SPF pass did not establish alignment with the visible sender.

**DKIM Analysis**

DKIM verification failed.

This means the simulated email did not have a valid DKIM authentication result.

A DKIM failure does not necessarily prove that the email was modified or tampered with. Further evidence would be needed to identify the reason for the failure.

**DMARC Analysis**

DMARC failed because SPF did not produce an aligned pass and there was no aligned DKIM pass.

This authentication failure, combined with the other indicators, increased my suspicion of the message.

These results are simulated. No original email headers were available for independent verification.

---

## 5. Incident Classification

**Classification: Suspected Credential Phishing**

I classified the email as suspected credential phishing based on the following evidence:

* The sender domain differed from the legitimate organisation's domain.
* The email used urgency and threatened account suspension.
* The recipient was directed to an unexpected password-reset link.
* SPF passed for a domain that did not align with the visible From domain.
* DKIM and DMARC failed in the simulated authentication results.

These indicators collectively support treating the email as suspicious.

However, I cannot confirm credential theft or malicious website behaviour without additional evidence.

---

## 6. Recommended Incident Response

Following my investigation, I would recommend the following actions.

**1. Protect the employee**

Advise the employee not to click the suspicious link or enter any credentials.

**2. Escalate the incident**

Report the suspicious email to the security team using the organisation's established reporting procedure.

Preserve relevant email evidence for further investigation.

**3. Identify additional recipients**

Check whether other employees received the same or similar email.

This would help determine whether the message forms part of a wider phishing campaign.

**4. Establish whether the user interacted with the email**

Ask whether the employee clicked the link or submitted credentials.

If credentials were entered, escalate immediately and follow the organisation's account-compromise response procedure, including securing the account and reviewing relevant sign-in activity.

**5. Consider preventative controls**

Recommend reviewing the sender domain and related indicators for monitoring or blocking, subject to validation and the organisation's security procedures.

---

## 7. Security Awareness Recommendations

I would recommend providing employees with phishing-awareness training.

The training should teach employees to:

* Check sender addresses and look for unexpected domains.
* Recognise urgency, fear and threats of account suspension.
* Avoid unexpected links requesting credentials.
* Verify suspicious requests through a known, trusted communication channel.
* Recognise the companies email domain and name format. 
* Report suspicious emails to the security team.
* Show employees what an original password reset from IT would look like.

These measures could help employees identify and report similar phishing attempts in the future.

---

## 8. Investigation Limitations

This investigation was conducted using fictional training material.

The email authentication results were hypothetical rather than extracted from real message headers.

The URL was not visited or scanned.

I did not have access to actual mail gateway logs, endpoint telemetry or user sign-in records.

Therefore, the classification remains suspected credential phishing rather than confirmed credential theft.

No real incident-response actions were performed.

---

## 9. Lessons Learned

This investigation helped me improve my understanding of email-based threats.

I learned that a sender-domain mismatch is a suspicious indicator but does not automatically prove that an email is malicious.

I also improved my understanding of SPF, DKIM and DMARC, particularly how SPF can pass while DMARC fails because of domain alignment.

The investigation reinforced the importance of combining multiple indicators before making an assessment.

I also learned the importance of distinguishing confirmed evidence from assumptions, documenting investigation limitations and following appropriate incident-response procedures.

---

**Final Assessment:** Suspected credential phishing.

**Recommended Outcome:** Escalate for further investigation and take appropriate protective actions in accordance with organisational procedures.
