# 📋 TODO - Manual Brute Force Method

This method simulates how an attacker might manually interact with the chatbot to uncover hardcoded logic, trigger vulnerabilities, or bypass validation using trial-and-error input patterns.

---

## 🔧 Phase 1: Reconnaissance & Setup

- [ ] Launch Juice Shop and navigate to the chatbot interface.
- [ ] Interact casually with the bot to observe response patterns.
- [ ] Note down:
  - Trigger keywords
  - Canned responses
  - Input sanitization (if any)
  - Input/output encoding techniques

---

## 🛠️ Phase 2: Input Injection Attempts

- [ ] Attempt to send known trigger terms:
  - `admin`, `flag`, `getFlag`, `root`, `bypass`
- [ ] Test various input casing (e.g., `Admin`, `ADMIN`, `aDmIn`)
- [ ] Try whitespace manipulation:
  - `admin `, ` admin`, ` a d m i n `
- [ ] Combine symbols and punctuation:
  - `admin!`, `admin?`, `admin#1`

---

## 📉 Phase 3: Rate Limiting & Behavioral Analysis

- [ ] Identify response delay patterns:
  - Is there a timeout after X failed inputs?
  - Does the chatbot behave differently after a keyword match?
- [ ] Try input spam at short intervals manually.
- [ ] Watch for:
  - Any session locking
  - Keyword-based keyword filtering

---

## 🧠 Phase 4: Pattern Learning

- [ ] Create a chart of bot responses for each payload attempt.
- [ ] Map potential decision trees:
  - If `x`, then bot responds `y`
- [ ] Detect if logic is based on keyword substring match, regex, or NLP.

---

## 🎯 Phase 5: Exploitation & Goal Trigger

- [ ] Once pattern discovered, craft the final brute-force payload.
- [ ] Enter the payload that triggers the **flag toast message**.
- [ ] Capture screenshots of:
  - Input used
  - Chatbot response
  - Toast message confirmation

---

## 🧩 Optional: Analyze JS

- [ ] Open DevTools → Sources → Locate chatbot scripts
- [ ] Look for:
  - Client-side NLP/token matcher
  - Hardcoded keyword triggers
- [ ] Use findings to reinforce brute-force logic

---

## ✅ Deliverables

- [ ] Final working payload
- [ ] Chatbot interaction sequence
- [ ] Flag screenshot (with timestamp)
- [ ] Technical write-up for README.md

