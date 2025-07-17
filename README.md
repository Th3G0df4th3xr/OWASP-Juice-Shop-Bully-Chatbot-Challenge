📁 README.md
markdown
Copy
Edit
# 🤖 OWASP Juice Shop - Bully Chatbot Challenge

Welcome to the **Bully Chatbot Challenge** in the OWASP Juice Shop! This challenge focuses on uncovering the **hidden Owner avatar** by interacting with a vulnerable chatbot interface using multiple exploitation techniques.

---

## 🎯 Challenge Objective

> **Goal:** Reveal the hidden **Owner's avatar** by manipulating the chat interface or exploiting backend/API vulnerabilities.

---

## 💡 Key Concepts

- DOM-based manipulation
- Web storage tampering (`localStorage`, `sessionStorage`)
- Client-side JavaScript hacking
- Hidden API endpoint discovery
- Automation using headless browsers (Selenium, Puppeteer)
- NLP prompt engineering to trick chatbots

---

## 🛠️ Exploitation Techniques

| Method                   | Category        | Tool/Stack                  | Description |
|--------------------------|------------------|-----------------------------|-------------|
| Dev-Tools-Network-Trick  | Manual/Intercept | Browser → DevTools → Network | Replay intercepted API calls revealing avatars |
| Direct-API-Call          | Backend Abuse    | `curl`, Postman, Python      | Hit internal endpoints directly bypassing frontend logic |
| Modifying-URL-Manually   | URL Parameter Tamper | Browser URL bar           | Trigger conditional rendering via URL manipulation |
| DOM-Manipulation-Trick   | Frontend DOM     | Browser Console (JS)         | Force hidden elements visible using CSS/JS |
| JS-Console-Automation    | Script Injection | Browser Console              | Fully automate avatar visibility with JavaScript |
| Manual-Brute-Force       | Logical Abuse    | Manual Inputs                | Iterate IDs/params until avatar renders |
| NLP-Trickery             | Prompt Engineering | Custom crafted sentences | Trick the chatbot into revealing or unlocking avatar |
| Selenium-or-Puppeteer    | Automation       | Python/Node.js + Selenium/Puppeteer | Scripted interaction with full rendering |
| Source-Code-Hack         | Static Analysis  | DevTools, Source Maps        | Analyze JS files to reverse engineer logic |
| Storage-Manipulation     | Client Storage   | DevTools → Application tab   | Tamper local/session storage flags to render avatar |

---

## 📂 Repository Structure

OWASP-Juice-Shop-Bully-Chatbot-Challenge/
├── Dev-Tools-Network-Trick/
├── Direct-API-Call/
├── Modifying-URL-Manually/
├── DOM-Manipulation-Trick/
├── JS-Console-Automation/
├── Manual-Brute-Force/
├── NLP-Trickery/
├── Selenium-or-Puppeteer/
├── Source-Code-Hack/
├── Storage-Manipulation/
├── README.md
└── TODO.md

yaml
Copy
Edit

Each folder contains scripts, markdown writeups, or PoCs for the respective attack method.

---

## 🚀 How to Use

1. Clone this repo:
   ```bash
   git clone https://github.com/<your-username>/OWASP-Juice-Shop-Bully-Chatbot-Challenge.git
   cd OWASP-Juice-Shop-Bully-Chatbot-Challenge
Pick any method folder to begin.

Follow the instructions or run the PoC provided inside.

Track your progress in TODO.md.

⚠️ Disclaimer
This repo is for educational and ethical hacking purposes only. Do not use these techniques on systems you don't own or have explicit permission to test.

📚 References
OWASP Juice Shop

OWASP Top 10 Web Vulnerabilities

MDN Web Docs - localStorage
