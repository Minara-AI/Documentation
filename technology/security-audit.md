---
description: >-
  Minara AI was audited by SlowMist from July 30 to August 19, 2025 (audit no.
  0X002508190001). Result: Passed. 23 findings, all 14 non-suggestion issues
  fixed, including 1 critical and 2 high.
---

# Security audit (SlowMist)

Minara AI has been security audited by the **SlowMist Security Team**. The audit ran from **July 30 to August 19, 2025**, and the result is **Passed**. SlowMist found 23 issues. All 11 critical, high, and low severity issues were fixed, and so were 3 of the 12 suggestions. Minara acknowledged the other 9 suggestions without fixing them in the audit window.

This page summarizes the report in plain text. The full report is available as a PDF: [Minara AI - SlowMist Audit Report](https://static.minara.ai/audit/Minara%20AI%20-%20SlowMist%20Audit%20Report.pdf).

## Audit at a glance

| Item                | Details                                                                          |
| ------------------- | -------------------------------------------------------------------------------- |
| Auditor             | SlowMist Security Team                                                           |
| Audit number        | 0X002508190001                                                                   |
| Audit period        | July 30, 2025 – August 19, 2025                                                  |
| Result              | **Passed**                                                                       |
| Scope               | The Minara AI web app at [minara.ai](https://minara.ai/) and its backend code    |
| Code version        | Repository `Minara-AI/minara-core-for-audit`, commit `f31bab713289177fb2c138c375c871f0e9ca1642` |
| Test methods        | Black-box testing (lead), grey-box testing (assist), plus automated scanning and manual review |
| Test items          | 78 items, all passed                                                             |
| Findings            | 23 in total: 1 critical, 2 high, 0 medium, 8 low, 12 suggestions                 |
| Status of findings  | 14 fixed, 9 acknowledged (all 9 are suggestions)                                 |

SlowMist's summary conclusion: *"During the audit, nine suggestions were acknowledged. All the other findings have been fixed."*

## What was tested

SlowMist tested Minara from an attacker's point of view, using the approach it calls "black box lead, grey box assists". The 78 test items cover:

* **Deposits and transfers:** deposit and transfer security, including fake deposit tests across supported chains.
* **Accounts and login:** registration, password reset, OAuth sign-in, account enumeration, lockout, two-factor authentication bypass, privilege escalation, and authorization bypass.
* **Sessions:** session management, cookies, session fixation, token leaks, logout, and session timeout.
* **Common web attacks:** cross-site scripting (XSS), cross-site request forgery (CSRF), SQL injection, XXE, SSRF, deserialization, template injection, code and command injection, and file inclusion.
* **APIs and business logic:** interface security, request forgery, rate limiting, workflow bypass, misuse protection, and file upload checks.
* **Infrastructure and transport:** network and platform configuration, SSL/TLS strength, SSL pinning, encrypted transmission of sensitive data, and security response headers.
* **Information exposure:** GitHub source code leaks, privacy data leaks, subdomain and service discovery, and backup or unlinked files.

All 78 test items are marked **Passed** in the report.

## Findings and their status

| No. | Finding                                                    | Severity   | Status       |
| --- | ---------------------------------------------------------- | ---------- | ------------ |
| N9  | Purchased token did not match the token shown in the AI trade dialog | Critical | Fixed |
| N3  | Login verification code could be brute-forced             | High       | Fixed        |
| N13 | Default slippage was too high (25%) and could not be changed | High     | Fixed        |
| N1  | Email code sending and verification used GET requests      | Low        | Fixed        |
| N2  | No human verification before sending email codes           | Low        | Fixed        |
| N4  | No two-factor authentication for login and sensitive actions | Low      | Fixed        |
| N5  | Logging out did not invalidate the session token on the server | Low    | Fixed        |
| N6  | API error responses revealed backend library details       | Low        | Fixed        |
| N8  | Valueless "fake deposit" tokens appeared in wallet activity | Low       | Fixed        |
| N10 | Wallet holdings showed the wrong chain for a token         | Low        | Fixed        |
| N11 | "Mention in next chat" passed the wrong token to chat      | Low        | Fixed        |
| N7  | Withdrawal fee was not shown before withdrawing            | Suggestion | Fixed        |
| N12 | Transaction confirmation lacked full details               | Suggestion | Fixed        |
| N18 | Older TLS versions were allowed                            | Suggestion | Fixed        |
| N14 | Swap API did not check the account balance first           | Suggestion | Acknowledged |
| N15 | No anti-phishing strategy                                  | Suggestion | Acknowledged |
| N16 | No anti-money-laundering (AML) strategy                    | Suggestion | Acknowledged |
| N17 | DNSSEC not configured for the domain                       | Suggestion | Acknowledged |
| N19 | Missing X-Frame-Options header                             | Suggestion | Acknowledged |
| N20 | Missing X-Content-Type-Options header                      | Suggestion | Acknowledged |
| N21 | Missing Strict-Transport-Security (HSTS) header            | Suggestion | Acknowledged |
| N22 | Missing Content-Security-Policy header                     | Suggestion | Acknowledged |
| N23 | CORS allowed requests from any origin                      | Suggestion | Acknowledged |

### What the most serious findings were

* **N9 (Critical), trade mismatch.** In one test, buying a token through an AI-recommended trade dialog resulted in a different token than the one shown. SlowMist recommended fixing the root cause so the purchased token always matches what the user sees. Status: Fixed.
* **N3 (High), login code brute force.** Email login codes had no limit on failed attempts, which made guessing a code practical. SlowMist recommended limiting failed attempts, shortening code validity, and making codes more complex. Status: Fixed.
* **N13 (High), slippage.** Default slippage was 25% and could not be changed, which exposed trades to sandwich attacks. SlowMist recommended adapting slippage to market conditions and letting users change it. Status: Fixed.

### What "Fixed" and "Acknowledged" mean

* **Fixed:** the issue was resolved, and SlowMist confirmed the fix. Minara did not provide a fixed version of the code for review, so SlowMist checked every fix by testing the live product from the outside (black-box testing).
* **Acknowledged:** Minara accepted the suggestion but did not fix it during the audit window. All 9 acknowledged items are suggestions, SlowMist's lowest level, which means "there are better practices for coding or architecture". None of them are critical, high, medium, or low severity vulnerabilities.

## Updates since the audit

Minara has kept working on several of the suggestions after the audit. The updates below are as of **November 3, 2026**. They come from Minara's own checks and were not re-verified by SlowMist.

| No. | Suggestion in the report                 | Update                                                                                                                                                                                                                                      |
| --- | ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| N23 | CORS allowed requests from any origin    | **Fixed.** The Minara API now only accepts cross-origin requests from Minara's own site. Requests from other websites are not allowed.                                                                                                      |
| N14 | Swap API did not check the account balance first | **Improved.** Before a trade is placed, Minara simulates it and checks your available balance. If you don't have enough, the order is stopped and you see how much you're short. Before a sell, Minara also checks that you hold enough of the token. |
| N15 | No anti-phishing strategy                | **Improved.** Minara can check whether a website or DApp is a phishing site, scan a token for scam risks such as honeypots, simulate a transaction before you sign it, and find risky token approvals for you to revoke. Minara also watches for common scam patterns, such as someone posing as support, a "safe account" transfer, or a recipient address that unexpectedly changes, and asks you to verify before you send funds. |

Separately, Minara's site still rejects connections over the outdated TLS 1.0 and 1.1 protocols, in line with the fix for N18.

## Severity levels used in the report

| Level      | Meaning in the SlowMist report                                                        |
| ---------- | ------------------------------------------------------------------------------------- |
| Critical   | Significant impact on the security of the project. Strongly recommended to fix.       |
| High       | Affects the normal operation of the project. Strongly recommended to fix.             |
| Medium     | Affects the operation of the project. Recommended to fix.                             |
| Low        | May affect operation in certain scenarios. The team should evaluate whether to fix.   |
| Weakness   | A theoretical risk that is extremely difficult to reproduce in practice.              |
| Suggestion | A better coding or architecture practice is available.                                |

## Limits of the audit

* The audit reflects Minara as it was during the audit period, July 30 to August 19, 2025. SlowMist states that it cannot judge the security of anything that happened or changed after the report was issued.
* Features released after August 2025 were not part of this audit.
* An audit lowers risk but does not guarantee that a product has no vulnerabilities, and it does not remove market risk.

## Frequently asked questions

**Has Minara been audited?**\
Yes. Minara AI was audited by the SlowMist Security Team from July 30 to August 19, 2025 (audit number 0X002508190001). The result is Passed.

**What did the audit cover?**\
The Minara AI web app at minara.ai and its backend code at commit `f31bab713289177fb2c138c375c871f0e9ca1642`, including deposits and transfers, accounts and login, sessions, APIs, trading flows, and infrastructure. SlowMist ran 78 test items, and all of them passed.

**Were the vulnerabilities fixed?**\
All critical, high, and low severity findings were fixed: 1 critical, 2 high, and 8 low. Of the 12 suggestions, 3 were fixed and 9 were acknowledged. SlowMist verified the fixes through black-box testing. Since the audit, Minara has also fixed the CORS suggestion (N23) and improved balance checks (N14) and anti-phishing protection (N15). See [Updates since the audit](#updates-since-the-audit).

**Were there any medium severity findings?**\
No. The audit found no medium severity issues.

**Where can I read the full report?**\
Download the PDF: [Minara AI - SlowMist Audit Report](https://static.minara.ai/audit/Minara%20AI%20-%20SlowMist%20Audit%20Report.pdf).

**How else does Minara protect users?**\
See [Wallet security](wallet-security.md) and [TEE-based data security](data-security.md). To report a vulnerability, see the [Minara Bug Bounty Program](minara-bug-bounty-program.md).
