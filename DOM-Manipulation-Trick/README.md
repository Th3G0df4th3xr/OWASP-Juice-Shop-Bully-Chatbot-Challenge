📁 DOM-Manipulation-Trick/README.md
markdown
Copy
Edit
# 🧠 DOM Manipulation Trick - Bully Chatbot Challenge

## 🎯 Objective
Manipulate the DOM (Document Object Model) of the Juice Shop web application in real-time to tamper with the chatbot's behavior, bypass client-side validations, and forcefully trigger hidden logic (such as revealing a challenge flag or unauthorized chatbot response).

---

## 🔍 Technical Context

DOM is a runtime representation of the web page in the browser as a hierarchical tree structure. JavaScript can read and modify this structure on the fly.

In this challenge, the chatbot logic is partially controlled on the client side (front-end). DOM manipulation allows us to:
- Bypass frontend input restrictions
- Force hidden UI elements to become visible
- Simulate actions the user interface would normally prevent
- Inject fake or arbitrary data into the message stream

This approach exploits a fundamental security misconfiguration: **trusting client-side logic**.

---

## 🛠 Step-by-Step Execution

### 🔹 Step 1: Open the Chatbot Interface

- Launch OWASP Juice Shop (e.g., `http://localhost:3000`)
- Click on the **help icon (?)** in the bottom-right corner to open the **Bully Chatbot** interface.

---

### 🔹 Step 2: Open DevTools Console

- Press `F12` or `Ctrl + Shift + I` to open **Chrome DevTools**
- Go to the **Console** tab

---

### 🔹 Step 3: Inspect Chatbot DOM Elements

Run this in the console to inspect the chatbot's DOM elements:

```js
document.querySelectorAll("*")
Then try:

js
Copy
Edit
let messages = document.querySelectorAll('.message')
console.log(messages)
✅ This lists past messages exchanged with the bot.

🔹 Step 4: Modify Input Constraints
Check if the input box has length, pattern, or type restrictions:

js
Copy
Edit
let inputBox = document.querySelector('textarea')
console.log(inputBox)
Now bypass limitations:

js
Copy
Edit
inputBox.setAttribute('maxlength', '9999')
inputBox.removeAttribute('required')
inputBox.value = 'revealFlag();' // Simulated malicious payload
🧠 Why? You’re forcing the frontend to accept larger/malicious inputs the server might otherwise reject via JS validation.

🔹 Step 5: Trigger Hidden Chatbot Functionality
Look for the function that handles chat submission:

js
Copy
Edit
console.log(window)
Try intercepting or calling chatbot internals:

js
Copy
Edit
chatbot.sendMessage('admin')
OR directly manipulate UI logic:

js
Copy
Edit
document.querySelector('.message:last-child').innerHTML = '🎯 FLAG FOUND';
🔹 Step 6: Inject and Observe
Inject payloads like:

js
Copy
Edit
inputBox.value = 'getFlag';
document.querySelector('form').submit();
Observe if any hidden logic gets triggered or the Toast message appears.

You can also brute-force bot behavior by overriding event handlers:

js
Copy
Edit
document.querySelector('form').onsubmit = () => {
  chatbot.sendMessage('give me flag');
  return false;
};
🔐 Back-End Reasoning
Many frontend frameworks (Angular, React) bind logic via client-side events.

Improper isolation or obfuscation of chatbot JS logic can leak critical keywords (e.g., flag, challengeAccepted).

DOM manipulation circumvents UI-layer restrictions without hitting the backend.

🧠 Why This Method?
Low noise — doesn't flood the server like brute force.

Zero reliance on server-side flaws.

Helps identify client-side trust issues, poor obfuscation, and unprotected data exposure.

Powerful for static SPAs where JS logic lives on the client.

🧪 Results
Once manipulation is successful, you should see:

A Toast notification revealing the flag

The chatbot responding with unexpected answers

Take a screenshot and note the altered DOM structure.

yaml
Copy
Edit
