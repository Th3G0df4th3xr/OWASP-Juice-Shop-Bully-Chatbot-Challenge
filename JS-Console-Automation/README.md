⚙️ JS-Console-Automation/README.md
markdown
Copy
Edit
# 🧠 JS-Console-Automation – Juice Shop DOM Hack

### 🔥 Challenge: OWASP Juice Shop – Hidden Privacy Policy Page

We're not just clicking links – we're **bypassing frontend logic and owning the DOM** using **pure JS console wizardry**. This method directly manipulates browser-side JS to unlock hidden features the app *doesn’t want you to see*.

---

## 🚀 Goal

Trigger the hidden Privacy Policy toast and navigate to the secret page using **JavaScript in the browser console**. No clicks. No UI fluff. Just code.

---

## 🛠️ Prerequisites

- 🧠 A browser with Developer Tools (Chrome or Firefox)
- ✅ Access to running Juice Shop instance (`http://localhost:3000` or any hosted target)
- 🧪 Basic JavaScript console knowledge

---

## 🧪 How It Works

The app hides the Privacy Policy logic behind frontend event listeners and broken routes. But since it **loads everything in the global scope**, we can force-execute it manually.

---

## 💻 Console Payload

```js
angular.element(document.querySelector('footer')).scope().showPrivacyPolicy()
🧬 Explanation: This command hijacks AngularJS scope and forces the frontend to reveal the hidden Privacy Policy popup and route.

🧨 Output Expected
✅ Toast: "Privacy Policy loaded."

✅ Page: /#/privacy-security/privacy-policy opens in browser

✅ Console: No errors if successful

⚠️ Pro Tips
Don’t paste this too early — wait until page fully loads (footer must exist).

If you see undefined, check if AngularJS is initialized.

Try refreshing and re-pasting if it fails.

📂 Structure
sql
Copy
Edit
JS-Console-Automation/
├── README.md         <-- You’re here
├── TODO.md           <-- Any future automation plans
└── screenshots/      <-- (Optional) DOM hack success screenshots
🧙‍♂️ Geek Notes
This isn’t a bug, it’s a challenge backdoor built for security learners.

Real-world apps can have hidden DOM elements accessible via console, and this trick mimics DOM injection-style XSS or dev mode manipulation.

🤘 Stay L33t
Console hacking is the art of controlling the browser’s mind — and you're now in command.
