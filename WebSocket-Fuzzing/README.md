📁 Storage-Manipulation/README.md
markdown
Copy
Edit
# 🗃️ Storage-Manipulation Hack – OWASP Juice Shop Bully Chatbot Challenge

This method leverages manipulation of browser-based client-side storage like `localStorage`, `sessionStorage`, or `IndexedDB` to unlock hidden UI elements such as the Privacy Policy link.

## 💡 Concept

Modern web apps store critical flags in the browser's storage to control feature visibility. By altering those flags manually, attackers can enable features not intended for general access.

## 🎯 Objective

Reveal and click the hidden Privacy Policy link to complete the **Bully Chatbot** challenge.

## 🛠️ How It Works

### 🔍 Frontend Side

- The visibility of certain features (like links) is toggled using local/session storage values.
- JavaScript on page load checks for specific flags (e.g., `showPrivacyPolicy === true`).

### 🔧 Backend Side

- No API call is involved in revealing the link.
- Once the link is clicked, the backend records the event and confirms challenge completion.

## 🧪 Sample Storage Injection

```js
localStorage.setItem("showPrivacyPolicy", "true");
location.reload();
✅ Success Indicator
Toast message appears: 🎉 Challenge Solved!

Privacy Policy link is visible in the footer.

This is one of the stealthiest methods to trigger frontend changes without network interaction or brute force. Ideal for scenarios involving frontend-only challenges.

vbnet
Copy
Edit
