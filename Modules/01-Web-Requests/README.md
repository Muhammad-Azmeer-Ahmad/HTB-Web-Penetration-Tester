# Module 01 — Web Requests

## What This Module Is About
HTTP is the protocol that powers all web communication. A client
sends a request to a server, the server processes it and returns
a response. Understanding this flow is the foundation of every
web pentest — if you don't know how requests work, you can't
manipulate them.

---

## HTTP Basics

Default port for HTTP is **80**, for HTTPS is **443**.

To reach a website we use a Fully Qualified Domain Name (FQDN)
written as a URL (Uniform Resource Locator).

### URL Structure

![URL Structure](Screenshots/url_structure.png)

| Component | Example | Description |
|-----------|---------|-------------|
| Scheme | `http://` `https://` | Protocol being used, ends with `://` |
| User Info | `admin:password@` | Optional credentials before the host |
| Host | `inlanefreight.com` | Hostname or IP address of the server |
| Port | `:80` | Separated from host by colon. Defaults: 80 (http), 443 (https) |
| Path | `/dashboard.php` | File or folder being requested |
| Query String | `?login=true` | Parameters passed to the server, starts with `?` |
| Fragments | `#status` | Processed client-side by browser to jump to a section |

---

## cURL

cURL (client URL) is a command-line tool for sending HTTP requests.
Essential for web pentesting — lets you craft, send, and inspect
requests without a browser.

### Commands I Used

```bash
# Basic GET request
curl http://info.cern.ch/

# Download a file silently
curl -s -O http://info.cern.ch/index.html

# View response headers
curl -i http://<SERVER_IP>:<PORT>/

# Verbose output — see full request and response
curl -v http://admin:admin@<SERVER_IP>:<PORT>/
```

---

## HTTP Basic Auth

Some pages use Basic HTTP Auth — handled by the webserver directly,
not a login form. The browser prompts for credentials before the
page loads.

### How to Handle With cURL

```bash
# Method 1 — -u flag
curl -u admin:admin http://<SERVER_IP>:<PORT>/

# Method 2 — credentials in URL
curl http://admin:admin@<SERVER_IP>:<PORT>/

# Method 3 — manually set Authorization header
# admin:admin in base64 = YWRtaW46YWRtaW4=
curl -H 'Authorization: Basic YWRtaW46YWRtaW4=' http://<SERVER_IP>:<PORT>/
```

Key observation: Basic Auth encodes credentials in Base64 — not
encrypted. Anyone intercepting the request can decode it instantly.
This is why HTTPS matters.

---

## GET Requests and Parameters

GET requests pass parameters directly in the URL after a `?`.

```bash
# Search request with GET parameter
curl 'http://<SERVER_IP>:<PORT>/search.php?search=le' \
  -H 'Authorization: Basic YWRtaW46YWRtaW4='

# Response
Leeds (UK)
Leicester (UK)
```

Useful trick — in browser DevTools Network tab, right-click any
request → Copy → Copy as cURL. Paste directly into terminal.
Saves time and gets exact headers the browser sent.

---

## Security Perspective

- Basic Auth credentials are just Base64 encoded — trivial to decode
- GET parameters are visible in URL, browser history, and server logs
- Always check DevTools Network tab on any web app assessment —
  reveals hidden endpoints, parameters, and backend calls
- The Authorization header can be set manually — useful for testing
  access control without going through login UI

---

## Key Takeaways

- HTTP default port 80, HTTPS 443
- URL has 7 components — each one is a potential attack surface
- cURL is the main tool for manual HTTP request testing
- Basic Auth = Base64, not encryption — never secure over HTTP
- GET parameters live in the URL — always logged, never secret