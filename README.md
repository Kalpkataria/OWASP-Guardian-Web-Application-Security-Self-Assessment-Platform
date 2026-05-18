# 🛡️ OWASP Guardian

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![Flask](https://img.shields.io/badge/Flask-2.3+-black?style=flat&logo=flask)
![OWASP](https://img.shields.io/badge/OWASP-Top%2010%202021-red?style=flat)
![University](https://img.shields.io/badge/NFSU-M.Sc%20Cyber%20Security-maroon?style=flat)

I built this project as part of my M.Sc. Cyber Security major project at NFSU, Gandhinagar. OWASP Guardian is a web application vulnerability scanner — you point it at a website, and it tells you what security issues it found, based on the OWASP Top 10 (2021) standard.

---

## What it does

It scans a target web app and checks for common vulnerabilities like SQL Injection, XSS, Broken Authentication, Missing Security Headers, Insecure File Uploads, and more. Results show up on a clean dashboard with severity levels, charts, and fix suggestions.

It also has an **Attack Simulation** mode where you can watch how attacks like SQL Injection or XSS would actually play out against a vulnerable app — step by step in a terminal-style view.

---

## VulnCorp

Since you can't just scan random websites, I built **VulnCorp** — a deliberately broken Flask app with 10 real vulnerabilities baked in. It runs locally on port 5001 and serves as the practice target for Guardian. Everything from SQL Injection to plaintext passwords to an admin panel you can bypass with `?admin=1`.

| Route | What's broken |
|-------|--------------|
| `/` | Reflected XSS via `?name=` param |
| `/login` | SQL Injection + default credentials |
| `/search` | UNION-based SQL Injection |
| `/comment` | Stored XSS |
| `/upload` | No file type or size validation |
| `/admin` | Bypassed with `?admin=1` |
| `/debug-info` | Leaks secret key + environment variables |
| `/api/users` | Unauthenticated API returning plaintext passwords |

> ⚠️ VulnCorp is intentionally insecure — never deploy it on a public server.

---

## How to run it

```bash
# Install dependencies
pip install flask requests beautifulsoup4

# Terminal 1 — start the vulnerable target
python vulnerable_dummy_app.py
# runs on http://127.0.0.1:5001

# Terminal 2 — start the scanner
python app.py
# runs on http://127.0.0.1:5000
```

Then open `http://127.0.0.1:5000`, sign up, enter `http://127.0.0.1:5001` as the target, and hit **Start Security Scan**.

---

## What's inside

- 🔍 **Full OWASP Top 10 (2021) scanning** — A01 through A10
- 📊 **Dashboard** — risk score, severity breakdown, donut & bar charts
- ⚔️ **Attack Simulation** — animated terminal showing SQL Injection, XSS, Auth bypass, and more
- 🕷️ **Web Crawler** — recursive link and form discovery
- 🍪 **Cookie Analyser** — checks HttpOnly, Secure, SameSite flags
- 🔎 **Subdomain Scanner** — via HackerTarget API
- 🛠️ **Fix Generator** — remediation code in Python, JS, PHP, and Java
- 📅 **Scheduled Scans** — daily, weekly, monthly automated scanning
- 🕵️ **Admin Finder** — common admin panel path enumeration
- 📄 **PDF Report Export** — downloadable security assessment report

---

## Scan results on VulnCorp

When Guardian scans VulnCorp, it finds:

- 🔴 **3 Critical/High** — SQL Injection, Broken Access Control, Sensitive Data Exposure
- 🟡 **8 Medium** — Missing Security Headers, CSRF, Insecure Upload
- 🟢 **9 Low** — Cookie flags, Open Redirect, Info Disclosure

**Overall Risk Level: CRITICAL** — exactly what you'd expect from a deliberately broken app.

---

## Project structure

```
OWASP_Guardian/
├── app.py                      # Main Guardian scanner
├── vulnerable_dummy_app.py     # VulnCorp — deliberate vulnerable target
├── requirements.txt
├── guardian.db                 # Auto-created on first run
├── vuln_test.db                # Auto-created on first run
├── templates/                  # HTML templates
└── static/                     # CSS, JS, assets
```

---

## Tech used

Python 3, Flask, SQLite3, requests, BeautifulSoup4, Chart.js

---

## ⚠️ Disclaimer

This tool is built strictly for educational use and authorized security testing only. Only scan systems you own or have explicit permission to test. The author is not responsible for any misuse.

---

## 👨‍💻 Author

**Kalp Kataria**
M.Sc. Cyber Security — Digital Forensics & Information Security
National Forensic Sciences University, Gandhinagar, Gujarat
kalpkataria0211@gmail.com
[GitHub](https://github.com/Kalpkataria)
