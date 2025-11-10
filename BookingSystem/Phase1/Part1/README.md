# 🧠 Penetration Testing Scenario – Initial Case

> [!NOTE]
> The material was created with the help of ChatGPT and Copilot.

## Starting Point

You are a **junior penetration tester** working for a cybersecurity company.
Your company has been contracted to test the following software system:

* The system is accessed via a **web browser**.
* Users can **register** and, after registration, **log in**.
* Once logged in, a user can act either as a **reservist** (regular user) or an **administrator**.
* Administrators can **add, delete, and edit** both resources and reservations.
* Administrators can **remove users** (reservists).
* Reservists can **book resources** if they are **over 15 years old**.
* Resources can be booked **by the hour**.
* The reservation list is **visible without logging in**, but **user identities are hidden**.
* The client company requires the system to be **GDPR-compliant**.
* The software developer claims to follow the principles of **Privacy by Design (PbD)**.

The system is being developed in **phases**.
In this first phase, you are testing **user registration** functionality.

You act as a **white-hat hacker**, using a **gray-box testing** approach.
Your task is to identify as many **anomalies** and **vulnerabilities** as possible and **categorize** your findings.

📚 Helpful references:

* [White-hat hacker (Google Search)](https://www.google.com/search?q=white+hat+hacker)
* [Gray-box testing (Google Search)](https://www.google.com/search?q=gray-box+testing)
* [NIST Vulnerability Definition](https://csrc.nist.gov/glossary/term/vulnerability)

---

### 🔍 Key Terms

**Anomaly:**

Any deviation from an accepted guideline or standard practice.
It may be intentional or accidental and might or might not affect security.
In this context, it can mean **illogical or inconsistent system behavior**.

**Vulnerability:**

**weakness or security flaw** in a system that can be exploited by an attacker to gain unauthorized access or cause other harm.

---

## 🧪 Penetration Testing Focus Areas

Perform penetration testing and write a **report** ([Check the template report](test_report_template.md)).

---

### 1. Authentication and Authorization

* Verify that user register processes are **secure**.
* Verify that user login processes are **secure**.
* Check that **roles and permissions** are properly defined and cannot be bypassed.

### 2. Input Validation

* Ensure that **all user inputs** are validated and sanitized.
* Look for possible **injection attacks** (e.g., SQLi, XSS).

### 3. Session Management

* Confirm that **sessions expire properly** and cannot be hijacked.
* Check that **session tokens** are complex and unpredictable.

### 4. Data Encryption

* Verify that sensitive data is **encrypted** both **in transit** and **at rest**.
* Ensure encryption algorithms are **up to date and secure**.

### 5. Error Handling and Logging

* Test that **error messages** do not expose sensitive information.
* Ensure **log files** contain enough information for incident tracing but avoid storing personal data.

### 6. Third-Party Components

* Review **external libraries and dependencies** for vulnerabilities.
* Check that third-party tools are **current and trustworthy**.

### 7. Usability and Performance

* Test that the system performs reliably under **load**.
* Evaluate **user experience** and whether security controls overly hinder usability.

### 8. GDPR Compliance

| Aspect                                | What to Test                                                    |
| ------------------------------------- | --------------------------------------------------------------- |
| **Data Minimization & Anonymization** | Only necessary data is collected and anonymized when possible.  |
| **Breach Notification**               | System can detect and report data breaches within **72 hours**. |
| **Data Encryption**                   | Personal data is encrypted during transfer and storage.         |
| **User Rights**                       | Users can request deletion, correction, or data portability.    |
| **Transparency**                      | Privacy policies are clear, accessible, and understandable.     |
| **Access Control**                    | Only authorized personnel can access personal data.             |

### 9. Privacy by Design (PbD) Principles

1. **Proactive, not reactive:** anticipate privacy risks before they occur.
2. **Privacy as the default setting:** data protection enabled by default.
3. **Privacy embedded into design:** integrated into system architecture.
4. **Full functionality:** balance privacy with usability and performance.
5. **End-to-end security:** protect data throughout its lifecycle.
6. **Transparency:** ensure trust through visible and verifiable privacy practices.
7. **Respect for user privacy:** provide clear options and consent mechanisms.

---

## 🧾 Penetration Testing Report Structure

[Check the template report](test_report_template.md)

---

# 🛡️ Quick guide to safe pen-testing

## 🔎 What is a penetration test?

A penetration test (pen test) is a controlled simulation of attacks against a system to find security problems **before** real attackers do. It includes planning, scanning, trying exploits (only when allowed), and writing a clear report with evidence and fixes.

---

## ⚖️ Legal & policy must-knows

You must **never** test systems you don’t have explicit permission to test. Doing so can be illegal and/or break contracts.

* **Get written permission.** If you don’t have a signed Rules-of-Engagement (RoE), don’t test. ✍️
* **Cloud providers:** Many providers (Azure, AWS, Google Cloud, etc.) **restrict** testing that affects shared infrastructure or other tenants. If a site is hosted on Azure, that **doesn’t automatically** give permission to test it — check the provider rules and the owner’s authorization. Your interpretation was sensible: providers often forbid aggressive or cross-tenant tests, but owners can usually test their *own* resources if they follow provider policies. ✅
* **No DoS unless explicitly allowed.** Flooding or destructive tests are typically banned. ❌
* **Personal data (GDPR/privacy):** Avoid real user data; if you must touch it, document lawful basis and protect evidence.

---

## ✅ Short checklist — do this **before** running tests 

1. **Written RoE** signed by the system owner (targets, allowed tests, schedule, contacts). ✍️
2. **Confirm ownership** of the target (account ID, tenant, or VM you control). 🔐
3. **Notify provider** if required (cloud hosts may ask you to notify/security-team). 📧
4. **Limit scope**: test only listed hosts/IPs; exclude third parties. 📍
5. **Backups & snapshots**: take them so you can revert after tests. 💾
6. **Emergency contacts**: ops, instructor, legal — reachable during tests. ☎️
7. **Evidence plan**: where you store logs/screenshots and how they’re protected. 🗂️🔒

---

## 🧪 Where to practice (safe options) 

Use isolated or purpose-built labs — do **not** test random internet sites.

* Local VMs / Docker / VirtualBox (host-only networks). 🖥️
* Institution-owned cloud tenant (only if you own it and have approvals). ☁️
* Training platforms: **TryHackMe, Hack The Box, OWASP Juice Shop, DVWA** — safe and legal. 🧩

---

## 🧰 What tools & actions are normally OK (with permission) 

* Passive recon (public info, DNS) — low risk. 🌐
* Authenticated scans (when you have credentials) — medium risk. 🔑
* Vulnerability scans — OK if scoped and scheduled. ⚠️
* Manual exploitation — only in lab/snapshotted environments or with explicit permission. 🔥
* DoS or wide network sweeps — usually forbidden. ❌

---

## 📝 Short RoE example sentence you can copy 

> “I request written authorization to perform controlled penetration testing on `vm-lab.example.local (10.0.0.10)` during 2025-11-25 09:00–16:00. Allowed activities: passive discovery, authenticated scanning, and controlled exploitation of intentionally vulnerable components. Not allowed: denial-of-service, testing of other tenants, or access to real user data. Contact: Instructor Name, +358 50 XXX XXXX.”

---

Great — here’s a clear, student-facing step-by-step guide for **setting up a safe testing environment**. It covers both options you requested: **(A) your own environment** and **(B) Centria KyberLab**. Written in plain English with emojis, quick commands, and small templates students can copy.

---

# Student guide — setting up your pen-test lab 🧰🔒

**You have two lab options:**

* **A) Your own environment** (Docker on your machine or in Kali)
* **B) Centria KyberLab** (institutional lab; follow lab rules)

In **both options**, you will use [this compose file](https://raw.githubusercontent.com/vheikkiniemi/CybersecurityAndDataPrivacyAutumn2025/refs/heads/main/BookingSystem/Phase1/Part1/docker-compose.yml) for Phase 1, Part 1

> ⚠️ Do **not** expose lab services to the public Internet. Keep everything local.

---

## A) Your own environment (Docker on your machine or in Kali) 🖥️

**Prerequisites:**

* Docker Desktop (Windows/Mac) or Docker Engine (Linux)
* A terminal (PowerShell, Terminal, bash)

---

### A1 — VM approach (Kali + Docker) — overview

* Use VirtualBox / VMware / Hyper-V.
* Inside the VM: install Kali (or Debian/Ubuntu plus tools) and Docker to run vulnerable apps and tools.

**Quick steps:**

**1. Download Kali ISO: [https://www.kali.org](https://www.kali.org) (instructor will provide link / checksum).**  
**2. Create VM in VirtualBox**  
**3. Install Kali and update**  

```bash
sudo apt update && sudo apt upgrade -y
```

**4. Install Docker:**  [Follow the instructions](https://docs.docker.com/engine/install/debian/)

**5. Create a clean lab folder**

```bash
mkdir -p ~/cyber-lab/phase1-part1
cd ~/cyber-lab/phase1-part1
```

**6. Download the compose file**  

**wget**

```bash
wget -O docker-compose.yml \
https://raw.githubusercontent.com/vheikkiniemi/CybersecurityAndDataPrivacyAutumn2025/refs/heads/main/BookingSystem/Phase1/Part1/docker-compose.yml
```

**7. (Optional) Check what will run**  

```bash
docker compose config
```

This validates the file and shows the final config.

**8. Start the lab**  

```bash
docker compose up -d
docker compose ps
```

Wait until all services show **“Up”**. Then open the app URLs shown in the compose file (commonly `http://localhost:8000`).

**9. Stop / reset**  

```bash
# Stop containers (keep data)
docker compose down

# Stop and remove volumes (fresh start)
docker compose down -v
```
**10. Test with penetration test tools (e.g. ZAP)**

### A2 — Windows + Docker Desktop — overview 🪟🐳

**Prerequisites:**

* Windows 10/11 (recent build).
* Docker Desktop installed (use WSL2 backend on Windows).
* PowerShell (run as Administrator for some steps).
* Git, curl or wget (optional).

**1. Install docker:** [Follow the instructions](https://docs.docker.com/desktop/setup/install/windows-install/)

**2. Add yourself to the docker-users group (Important!)**

Docker Desktop creates a local group called `docker-users`. Add your Windows user to that group so you can run Docker without permission issues.

Open **PowerShell as Administrator** and run:

```powershell
# add current user to docker-users
Add-LocalGroupMember -Group "docker-users" -Member $env:UserName
```

After this, **log out and log back in** (or reboot) so the group membership takes effect.

> If `Add-LocalGroupMember` isn't available (older Windows), use Computer Management → Local Users and Groups → Groups → docker-users → Add your user.

**3. Start Docker Desktop**

* Launch **Docker Desktop** and let it finish initialization (WSL2 integration may install/ask to enable).
* Check Docker is working in PowerShell (no admin required now):

```powershell
docker version
docker compose version
```

**4. Prepare a working folder & download the compose file**  

Open PowerShell (regular user) and run:

```powershell
mkdir $HOME\cyber-lab\phase1-part1
cd $HOME\cyber-lab\phase1-part1

# download compose file (PowerShell)
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/vheikkiniemi/CybersecurityAndDataPrivacyAutumn2025/refs/heads/main/BookingSystem/Phase1/Part1/docker-compose.yml" -OutFile docker-compose.yml
```

**5. Start the lab stack (run as regular user):**

```powershell
docker compose up -d
docker compose ps
```

Wait until services show `Up`. Open any mapped URLs in your browser (usually `http://localhost:8000`). Check the compose file for exact ports.

**6. Stop & cleanup**

```powershell
# stop, keep volumes
docker compose down

# stop and remove volumes (fresh reset)
docker compose down -v
```

**7. Quick troubleshooting**

* `docker compose` not found → restart Docker Desktop; ensure PATH is updated.
* Permission / access denied → you probably need to log out/in after adding to `docker-users`. Reboot if needed.
* Ports already in use → run `Get-Process -Id (Get-NetTCPConnection -LocalPort <port>).OwningProcess` or change mappings in an override.
* Container health problems → `docker logs <service-name>` and `docker compose ps`.

**8. Safety reminders**

* Make sure compose file and any override do **not** publish ports to the public network (bind to `127.0.0.1` when possible).
* Keep snapshots / backups of any data you need.
* Only test targets listed in your RoE.

---

## B) Centria KyberLab 🏫

1. **Get access** via instructor/lab portal (you’ll receive credentials and lab rules).
2. **Start the provided lab stack** (services are preconfigured).
3. **Collect evidence** the same way (ZAP report + screenshots).
4. **Follow lab policies** strictly (no external testing, no internet exposure).

---

## Safety reminders ⚠️

* **Scope & permission:** Only test local applications.
* **No DoS:** Don’t run destructive tests unless explicitly allowed.
* **Local only:** Bind ports to `127.0.0.1` unless your instructor says otherwise.
* **Privacy:** Do not collect real personal data.
* **Clean up:** Use `docker compose down -v` to reset when done.

---

## Quick troubleshooting 🛠️

* **“Ports already in use”** → stop whatever uses the port, or change mapping in an override.
* **Container restarts** → `docker logs <service-name>` and check environment variables or volumes.
* **App not reachable** → confirm the port mapping and URL, run `docker compose ps`.