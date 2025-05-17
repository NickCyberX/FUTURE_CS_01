# 🔐 Web Application Security Testing Report

This repository documents a hands-on security testing internship project conducted on **DVWA (Damn Vulnerable Web Application)** using tools such as **Burp Suite**, **SQLMap**, and **OWASP ZAP**.

The objective was to identify and exploit common web application vulnerabilities — including **SQL Injection**, **Cross-Site Scripting (XSS)**, and **Authentication Flaws** — and propose appropriate mitigation strategies.

---

## 🧰 Tools Used

- **Burp Suite** (Community Edition)
- **Kali Linux**
- **DVWA (Docker-based setup)**
- **SQLMap**
- **Firefox (proxy-configured)**
- **OWASP ZAP**

---

## 🛡️ Vulnerabilities Tested & Findings

### 1️⃣ SQL Injection (SQLi)

- **Location:** DVWA → SQL Injection module
- **Method:** Manual injection via user ID input field (`?id=` parameter)
- **Payloads Tested:** `' OR '1'='1`, `' UNION SELECT null, version()--`, etc.
- **Outcome:**
  - Retrieved database version and user data using `UNION SELECT`
  - Successfully demonstrated data leakage due to unparameterized SQL queries

---

### 2️⃣ Cross-Site Scripting (XSS)

- **Location:** DVWA → XSS (Reflected)
- **Payloads:** `<script>alert("XSS")</script>`, `<img src=x onerror=alert('XSS')>`
- **Outcome:**
  - JavaScript executed in browser when payload was reflected into the page
  - Verified DOM-based and reflected XSS with unsanitized user input
- **Risk:** Could allow session hijacking, defacement, or malicious redirection

---

### 3️⃣ Authentication Flaws (Brute Force Attack)

- **Location:** DVWA → Brute Force module
- **Tool Used:** Burp Suite Intruder
- **Method:**
  - Captured login request and configured username/password payloads
  - Detected valid credentials based on response header (`Location: index.php`)
- **Outcome:**
  - No lockout, rate limiting, or CAPTCHA mechanisms
  - Successful brute-force login using dictionary attack

---

## 📁 Files Included

- `BurpSuite BruteForce Report.docx` – Brute-force attack documentation
- `DVWA Security Test Report.docx` – Report on XSS and SQL Injection
- `README.md` – This documentation file

---

## 🧯 Mitigation Strategies (Overview)

| Vulnerability    | Mitigation Recommendation                                       |
|------------------|------------------------------------------------------------------|
| SQL Injection     | Use parameterized queries / prepared statements                |
| XSS              | Sanitize & encode all user input/output                         |
| Brute Force      | Implement account lockouts, rate limiting, and CAPTCHA          |
| Authentication   | Enforce strong password policies and multi-factor authentication|

---

## ⚠️ Disclaimer

> This project was conducted in a **controlled lab environment** using intentionally vulnerable applications for learning purposes only. Do **not** replicate these techniques on real systems without proper authorization.

---

## 📬 Contact

**Author:** NickCyberX  
**Internship Focus:** Cybersecurity | Penetration Testing | Ethical Hacking  
**Certifications:** Cisco Cybersecurity Badge • CCNA: Introduction to Networks  
**Tools:** Burp Suite • OWASP ZAP • SQLMap • DVWA • Kali Linux

**LinkedIn:** [tobechukwu-nicholas-460975245](https://www.linkedin.com/in/tobechukwu-nicholas-460975245)

---

⭐ **Star** this repository if you find it useful for learning, demonstrations, or building your cybersecurity portfolio.
