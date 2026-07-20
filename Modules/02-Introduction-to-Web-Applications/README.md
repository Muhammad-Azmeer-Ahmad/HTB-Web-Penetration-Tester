# Module 02 — Introduction to Web Applications


## What This Module Is About
Understanding how web applications are built, how they differ from
static websites, and why they are such a massive attack surface.
Before you attack something you need to understand what it is.

## Sections
- [x] Introduction
- [ ] More sections coming as I progress...

## Web App vs Static Website
- Static = same for everyone, manually updated, Web 1.0
- Web App = dynamic, changes per user, fully functional, Web 2.0

## Why Web Apps Are a Massive Attack Surface
- Accessible by anyone with a browser worldwide
- Constantly changing — a single code change can introduce a critical vuln
- Linked to databases with sensitive data
- Automated tools make scanning and attacking easier than ever

## Real World Attack Examples

| Vulnerability | Real World Impact |
|---------------|-------------------|
| SQL Injection | Extract AD usernames → password spray VPN/email portal |
| File Inclusion | Read source code → find hidden pages → RCE |
| File Upload | Upload malicious file as profile picture → full server control |
| IDOR | Change `/user/701/edit` to `/user/702/edit` → access another user |
| Broken Access Control | Register with `roleid=0` in POST body → instant admin account |

---

## Web Application Layout

Three main categories every web app is built around:

| Category | Description |
|----------|-------------|
| Infrastructure | Database, servers, hosting setup |
| Components | UI/UX, Client, Server parts |
| Architecture | Relationships between all components |

---

## Infrastructure Models

### Client-Server
Most common. Server hosts the app, browser is the client.
Front end runs in browser, back end runs on server.

### One Server
Everything on one machine — app, database, all of it.
Riskiest model. One breach = everything compromised.
Classic "all eggs in one basket."

### Many Servers — One Database
Multiple web servers, single shared database.
If one server is compromised, others still run.
Better segmentation than one server model.

### Many Servers — Many Databases
Each app gets its own database, sometimes its own DB server.
Best security — proper segmentation and access control.
Used for redundancy too — backup runs if primary goes down.

---

## Three Tier Architecture

| Layer | What It Does |
|-------|-------------|
| Presentation | What user sees — HTML, CSS, JS in browser |
| Application | Processes requests, checks auth and privileges |
| Data | Stores and retrieves data for the application |

---

## Microservices and Serverless

**Microservices** — app broken into independent components,
each doing one job (payments, search, ratings etc).
Stateless communication between them.
Can be written in different languages and still talk to each other.

**Serverless** — runs in cloud containers like Docker on AWS/GCP/Azure.
No server management needed — cloud handles it all.

---

## Security Perspective
- One server model = single point of failure and single point of compromise
- Architecture flaws are just as dangerous as code flaws
- Missing RBAC = users accessing admin features without a single line
  of vulnerable code — it is a design error not a coding error
- If you breach a server and can not find the database — it is
  probably on a separate server. Keep enumerating.

## Status
🔄 In progress — updating as I complete each section