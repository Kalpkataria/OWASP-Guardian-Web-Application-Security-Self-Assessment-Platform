# OWASP-Guardian-Web-Application-Security-Self-Assessment-Platform

# 🛡️ OWASP Guardian — Automated Web Application Vulnerability Scanner

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![Flask](https://img.shields.io/badge/Flask-2.3+-black?style=flat&logo=flask)
![OWASP](https://img.shields.io/badge/OWASP-Top%2010%202021-red?style=flat)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)
![University](https://img.shields.io/badge/NFSU-M.Sc%20Cyber%20Security-maroon?style=flat)

> An automated web application vulnerability scanner aligned with the **OWASP Top 10 (2021)** framework, built with Python & Flask. Developed as a Major Project for M.Sc. Cyber Security at **National Forensic Sciences University (NFSU), Gandhinagar**.

---

## 📌 About The Project

**OWASP Guardian** is a locally deployable, Flask-based web application security scanner that automatically detects vulnerabilities across all ten OWASP Top 10 (2021) categories. It combines active HTTP-based probing, header analysis, SQL error detection, XSS pattern matching, cookie security inspection, and sensitive path enumeration into a single unified platform.

The project includes **VulnCorp** — a deliberately vulnerable companion web application with 10 real, exploitable vulnerabilities — designed as a controlled, ethical testing target for Guardian.

---

## ✨ Features

- 🔍 **Full OWASP Top 10 (2021) Coverage** — A01 through A10
- 📊 **Interactive Dashboard** — severity breakdown, donut chart, bar chart, risk score
- ⚔️ **Attack Simulation Module** — animated terminal-style attack demonstrations
- 🕷️ **Web Crawler** — recursive link and form discovery
- 🍪 **Cookie Analyser** — HttpOnly, Secure, SameSite flag inspection
- 🔎 **Subdomain Scanner** — via HackerTarget API integration
- 🛠️ **Fix Generator** — language-specific remediation code (Python, JS, PHP, Java)
- 📅 **Scheduled Scans** — daily, weekly, monthly automated scanning
- 🕵️ **Admin Finder** — common admin panel path enumeration
- 📄 **PDF Report Export** — professional security assessment reports
- 🎯 **VulnCorp Target App** — 10 intentional vulnerabilities for local testing

---

## 🚨 Vulnerabilities Detected

| OWASP Code | Category | Detection Method |
|------------|----------|-----------------|
| A01 | Broken Access Control | Sensitive path enumeration, IDOR checks |
| A02 | Cryptographic Failures | HTTP detection, weak crypto patterns |
| A03 | Injection | SQL error string matching, XSS pattern detection |
| A04 | Insecure Design | Logic flaw indicators |
| A05 | Security Misconfiguration | Header analysis, debug mode detection |
| A06 | Vulnerable Components | Library version detection |
| A07 | Auth Failures | Cookie flags, lockout testing, JWT checks |
| A08 | Data Integrity Failures | CDN integrity check absence |
| A09 | Logging Failures | Error exposure detection |
| A10 | SSRF | Open redirect detection |

---

## 🏗️ Project Structure


---

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.x
- pip

### Step 1 — Clone the repository
```bash
git clone https://github.com/Kalpkataria/OWASP-Guardian.git
cd OWASP-Guardian
```

### Step 2 — Install dependencies
```bash
pip install flask requests beautifulsoup4
```

### Step 3 — Run both apps in separate terminals

**Terminal 1 — Start VulnCorp (vulnerable target):**
```bash
python vulnerable_dummy_app.py
# Runs on http://127.0.0.1:5001
```

**Terminal 2 — Start Guardian (scanner):**
```bash
python app.py
# Runs on http://127.0.0.1:5000
```

### Step 4 — Open Guardian in browser

- Sign up / Log in
- Enter target URL: `http://127.0.0.1:5001`
- Click **Start Security Scan**

---

## 🖥️ Screenshots

| Dashboard | Scan Results | Attack Simulation |
|-----------|-------------|-------------------|
| ![Dashboard](screenshots/dashboard.png) | ![Scan](screenshots/scan.png) | ![Sim](screenshots/simulation.png) |

---

## 🎯 VulnCorp — Test Target

VulnCorp is the companion deliberately vulnerable application included for safe, legal, local testing.

| Route | Vulnerability |
|-------|--------------|
| `/?name=<script>alert(1)</script>` | Reflected XSS |
| `/login` | SQL Injection + Broken Auth |
| `/search?q=` | SQL Injection (UNION) |
| `/comment` | Stored XSS |
| `/upload` | Insecure File Upload |
| `/admin?admin=1` | Broken Access Control |
| `/redirect?url=` | Open Redirect |
| `/debug-info` | Sensitive Data Exposure |
| `/api/users` | Unauthenticated API |

> ⚠️ **VulnCorp is intentionally insecure. Never deploy it on a public server.**

---

## 🔬 Scan Results (VulnCorp)

Guardian successfully detected **20 issues** on VulnCorp:

- 🔴 **3 Critical/High** — SQL Injection, Broken Access Control, Sensitive Data Exposure
- 🟡 **8 Medium** — Missing Security Headers, CSRF, Insecure Upload
- 🟢 **9 Low** — Cookie flags, Open Redirect, Info Disclosure

**Overall Risk Level: CRITICAL**

---

## 🛠️ Tech Stack

- **Backend:** Python 3.x, Flask 2.3+
- **Database:** SQLite3
- **HTTP Scanning:** requests, BeautifulSoup4
- **Frontend:** HTML5, CSS3, IBM Plex Sans/Mono
- **Charts:** Chart.js
- **Security:** SHA-256 password hashing, Flask sessions

---

## ⚠️ Disclaimer

> This tool is developed **strictly for educational and authorized security testing purposes**. Use OWASP Guardian only against systems you own or have explicit written permission to test. The authors are not responsible for any misuse or damage caused by this tool.

---

## 👨‍💻 Author

**Kalp Kataria**
M.Sc. Cyber Security (Digital Forensics & Information Security)
National Forensic Sciences University, Gandhinagar, Gujarat
📧 kalpkataria0211@gmail.com
🔗 [GitHub](https://github.com/Kalpkataria) | AIR 27 — NFAT

---

## 🏫 Institution

**School of Cyber Security & Digital Forensics**
National Forensic Sciences University (NFSU)
Gandhinagar – 382009, Gujarat, India
*(An Institution of National Importance, Ministry of Home Affairs, Government of India)*

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

*Made with ❤️ for cybersecurity education at NFSU*


