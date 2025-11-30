# Rinu Cybersecurity Portfolio

> This document contains a ready-to-use GitHub portfolio structure, website files, resume, and 3 sample project templates (SOC investigation, Web App Pentest, Threat Hunting). Copy files into a repository named `rinu-cybersecurity-portfolio` and publish using GitHub Pages if you want a public site.

---

## Repo structure

```
rinu-cybersecurity-portfolio/
├── README.md
├── LICENSE
├── assets/
│   ├── profile.jpg           # replace with your photo
│   ├── logos/
│   └── certifications/
├── resume.pdf               # optional final PDF
├── resume.md
├── projects/
│   ├── soc-investigation/
│   │   ├── report.md
│   │   ├── splunk-queries.md
│   │   └── screenshots/
│   ├── web-pentest/
│   │   ├── methodology.md
│   │   ├── findings.md
│   │   └── poc-screenshots/
│   └── threat-hunting/
│       ├── hypothesis.md
│       ├── queries.md
│       └── report.md
├── docs/
│   ├── sample-reports/
│   └── cheatsheets/
└── website/
    ├── index.html
    ├── about.html
    ├── projects.html
    └── assets/
        └── styles.css
```

---

## README.md (starter)

```md
# Rinu Das — Cybersecurity Portfolio

Welcome to my cybersecurity portfolio. This repository contains my resume, project write-ups, detection queries, and a simple GitHub Pages website.

## About
I am a cybersecurity enthusiast focused on SOC analysis, threat hunting, and web application penetration testing. I work with Splunk, Elastic, Sysmon, and common pentesting tools.

## Projects
- **SOC Investigation** — incident triage and Splunk searches.
- **Web Application Pentest** — OWASP vulnerabilities on Juice Shop/DVWA.
- **Threat Hunting** — Sysmon-based hunting and detection queries.

## How to use
1. Replace `assets/profile.jpg` with your photo.
2. Update `resume.md` and `resume.pdf`.
3. Edit project reports inside `projects/` with your screenshots and findings.
4. To publish the website: push to GitHub and enable GitHub Pages from the `website/` folder.

Contact: YOUR_EMAIL | LinkedIn: YOUR_LINKEDIN | GitHub: YOUR_GITHUB
```

---

## website/index.html (simple, accessible)

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Rinu Das — Cybersecurity Portfolio</title>
  <link rel="stylesheet" href="assets/styles.css">
</head>
<body>
  <header class="hero">
    <img src="../assets/profile.jpg" alt="Rinu Das" class="avatar">
    <h1>Rinu Das</h1>
    <p>SOC Analyst & Penetration Tester (Aspiring)</p>
    <p><a href="mailto:your-email@example.com">your-email@example.com</a> • <a href="https://github.com/your-github">GitHub</a> • <a href="https://www.linkedin.com/in/your-linkedin">LinkedIn</a></p>
  </header>

  <section>
    <h2>Skills</h2>
    <ul>
      <li>SIEM: Splunk, QRadar, Elastic</li>
      <li>Tools: Nmap, Burp Suite, Nuclei, Sysmon, OSQuery</li>
      <li>Scripting: Bash, Python</li>
      <li>Frameworks: MITRE ATT&CK mapping, OWASP</li>
    </ul>
  </section>

  <section>
    <h2>Projects</h2>
    <ul>
      <li><a href="projects.html#soc">SOC Investigation</a></li>
      <li><a href="projects.html#web">Web Application Pentest</a></li>
      <li><a href="projects.html#hunt">Threat Hunting</a></li>
    </ul>
  </section>

  <footer>
    <p>© 2025 Rinu Das</p>
  </footer>
</body>
</html>
```

---

## website/assets/styles.css (very simple)

```css
body{font-family:system-ui,Segoe UI,Roboto,Helvetica,Arial;max-width:900px;margin:2rem auto;padding:0 1rem;color:#111}
.hero{text-align:center}
.avatar{width:120px;border-radius:50%}
section{margin-top:1.5rem}
```

---

## resume.md (editable resume template)

```md
# Rinu Das

**Email:** your-email@example.com  •  **Phone:** +91-XXXXXXXXXX

## Summary
Cybersecurity enthusiast with hands-on experience in SOC analysis, log investigation, and web application testing. Comfortable with Splunk, Sysmon, Nmap, and Python scripting.

## Skills
- SIEM: Splunk, QRadar
- Pentesting: Burp Suite, Nmap, OWASP
- Scripting: Python, Bash
- Frameworks: MITRE ATT&CK

## Education
- BSc / Diploma — Institution — Year

## Certifications
- TryHackMe — Path/Rooms
- Google/IBM Cybersecurity basics (add dates)

## Projects
- SOC Investigation — brief line
- Web App Pentest — brief line
- Threat Hunting — brief line

## Languages
- English, Malayalam (native)
```

---

## projects/soc-investigation/report.md (SOC Investigation template)

```md
# SOC Investigation — Sample Report

**Scope:** Investigate suspicious authentication anomalies on host `HOSTNAME`.

## Summary
Short summary of the incident, timeline, and impact.

## Evidence & Timeline
- 2025-11-20 09:12 — Multiple failed logins (source IP x.x.x.x)
- 2025-11-20 09:17 — Successful login from new geolocation

## Splunk Queries
See `splunk-queries.md`.

## Findings
- Brute-force attempt confirmed.
- Weak password reuse detected.

## Recommendations
- Enforce MFA for all accounts.
- Implement account lockout on failed attempts.
```

---

## projects/soc-investigation/splunk-queries.md

```md
# Useful Splunk Searches

1) Failed logins (Windows Security Event 4625):
```

index=wineventlog EventCode=4625 | stats count by Account_Name, src

```

2) Successful logins from rare countries:
```

index=wineventlog EventCode=4624 | iplocation src | where Country != "India" | stats count by Account_Name, Country

```

3) Suspicious process execution (Sysmon):
```

index=sysmon EventCode=1 Process_Name=cmd.exe OR Process_Name=powershell.exe | stats count by host, Process_Name, CommandLine

```
```

---

## projects/web-pentest/methodology.md

```md
# Web Application Pentest — Methodology

1. Reconnaissance (subdomain enumeration, port scan)
2. Automation (nuclei scans, nikto)
3. Manual testing using Burp Suite
4. Verify and create proof-of-concept (POC) for each finding
```

---

## projects/web-pentest/findings.md

```md
# Findings — Web Pentest (Sample)

## Finding 1 — SQL Injection (High)
**URL:** /product?id=23
**Description:** Unsanitized parameter leads to SQLi.
**PoC:** `id=23' OR '1'='1` — returned all products.
**Impact:** Data exposure.

## Finding 2 — Cross-Site Scripting (XSS) (Medium)
**URL:** /search?q=
**PoC:** `<script>alert(1)</script>`
```

---

## projects/threat-hunting/hypothesis.md

```md
# Threat Hunting — Hypothesis

Hypothesis: Adversaries are using living-off-the-land binaries (LOLBins) to execute commands on endpoints. We will hunt for suspicious commandlines invoking cmd.exe/powershell.exe with base64 arguments or downloader patterns.
```

---

## projects/threat-hunting/queries.md

```md
# Hunting Queries (Splunk)

1) PowerShell encoded command detection:
```

index=wineventlog EventCode=4688 New_Process_Name=powershell.exe CommandLine="* -enc *" | stats count by host, Account_Name

```

2) Unusual wmic / bitsadmin activity:
```

index=wineventlog EventCode=4688 (CommandLine="*bitsadmin*" OR CommandLine="*wmic*") | stats count by host, CommandLine

```
```

---

## LICENSE (MIT) — simple license placeholder

```txt
MIT License

Copyright (c) 2025 Rinu Das

Permission is hereby granted, free of charge, to any person obtaining a copy
...
```

---

## HOW TO PUBLISH (quick steps)

1. Create a new GitHub repo named `rinu-cybersecurity-portfolio`.
2. Push this repo contents.
3. In GitHub -> Settings -> Pages -> choose `main` branch / `/website` folder and Save.
4. Your site will be available at `https://your-github-username.github.io/rinu-cybersecurity-portfolio/`.

---

## NOTES & NEXT STEPS

* Replace all placeholder text (email, links, screenshots).
* Add real screenshots into `projects/*/screenshots` and `poc-screenshots`.
* If you want, I can:

  * Generate a PDF portfolio from `resume.md` and project reports.
  * Create a ready-to-push GitHub repo (zip) with these files.
  * Make a more polished React + Tailwind single-page portfolio.

---

*End of template.*
