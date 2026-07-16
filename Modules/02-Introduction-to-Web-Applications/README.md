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

## Status
🔄 In progress — updating as I complete each section