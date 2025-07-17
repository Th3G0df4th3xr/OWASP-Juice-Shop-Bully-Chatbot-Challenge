📂 Manual-Brute-Force/README.md
markdown
Copy
Edit
# 🔐 Manual Brute Force - OWASP Juice Shop Privacy Policy Challenge

## 🧠 Objective
To manually discover and access the **hidden Privacy Policy** route by systematically guessing and testing endpoint paths via the browser or tools, bypassing UI restrictions.

---

## 🧬 Strategy

The goal is to enumerate non-linked client-side routes by **manually guessing endpoint paths** that may not be discoverable through UI clicks or standard navigation. This is often referred to as "brute-force discovery" and is a useful technique in black-box penetration tests.

This works because **Single Page Applications (SPA)** like Juice Shop built with **Angular** rely on client-side routing (`/#/route-name`) — meaning hidden pages may still be reachable if their route is known.

---

## 🧪 Methodology

### 🔹 Step 1: Understand Angular SPA Routing
Juice Shop uses **AngularJS**, where routes are registered on the client and follow a pattern:
http://<target-ip>:3000/#/<route>

markdown
Copy
Edit
Routes such as:
- `/about`
- `/score-board`
- `/contact`
...are linked and visible.

But many others exist like:
- `/administration`
- `/complain`
- `/privacy-security/privacy-policy`

These may not be directly accessible via the UI.

---

### 🔹 Step 2: Perform Manual Brute Force

#### 📌 Tools:
- Web Browser (Chromium/Firefox)
- Wordlist (optional: create one based on context)
- DevTools > Network Tab (to watch XHR requests)

#### 🧩 Manual Technique:
1. Navigate to the base app:
http://localhost:3000/

mathematica
Copy
Edit

2. In the browser URL bar, manually modify the route:
http://localhost:3000/#/privacy-security/privacy-policy

yaml
Copy
Edit

3. Hit Enter.

4. Expected:
- Route loads (even if no direct link exists)
- Toast message: `Privacy Policy loaded`
- DevTools Console: Possibly logs AngularJS route change

---

## 🔄 Alternate Enumeration Technique

1. Use the browser **autocomplete** or typing `/` after `#/` to see any possible route caching.

2. Enable **Angular Batarang** browser extension to inspect the full `$route` or `$state` tree.

---

## 🛠️ Optional Tools

### Option 1: Dirbuster/ffuf for Route Discovery (not typical for SPAs)
```bash
ffuf -u http://localhost:3000/#/FUZZ -w wordlist.txt
Note: This is NOT effective for #/ hash-based routes unless interpreted by a headless browser. Tools like Puppeteer are better for these.

📚 Technical Concepts Involved
Term	Explanation
SPA (Single Page Application)	All routes are loaded in one page, dynamic rendering via JavaScript
Angular Routing	Handled client-side using hash-based (#/) or path-based (/) URLs
Manual Brute Forcing	Trying known/guessed route names to discover hidden functionality
Toast Notification	Temporary messages triggered by Angular scope changes (success indicators)

🛡️ Security Perspective
This method emulates an unauthenticated attacker attempting to:

Access hidden routes

Test for security-through-obscurity failures

Confirm improper access control on internal pages

Any route not protected by proper authorization checks is a potential risk.

✅ Validation Criteria
 Route /privacy-security/privacy-policy is discoverable manually

 No UI link is exposed to access it

 Challenge toast Privacy Policy loaded confirms success

📌 Notes
This is one of the simplest yet powerful ways to bypass UI limitations.

It is not automation — but serves as a baseline for scripting approaches later (e.g., Puppeteer/Selenium).
