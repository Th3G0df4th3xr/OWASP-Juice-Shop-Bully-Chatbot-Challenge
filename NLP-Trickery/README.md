📁 NLP-Trickery/README.md
markdown
Copy
Edit
# 🧠 NLP-Trickery - Chatbot Abuse for Privacy Policy Trigger

## 🎯 Objective
Exploit the natural language processing layer of the chatbot to indirectly trigger the hidden **Privacy Policy** route in Juice Shop using semantically aligned queries that map to the "privacy-policy" intent.

---

## 📌 What’s Happening Internally

### 🔍 Frontend
- The chatbot is a floating widget likely implemented using **Angular** and relies on **event-based input handling**.
- Input box captures user messages and sends them to the backend through WebSocket or REST.
- On detecting the **intent** `privacy-policy`, the frontend uses `window.location.href` to navigate to `/#/privacy-security/privacy-policy`.

### 🧠 Backend (NLP Intent Mapping)
- Juice Shop uses **intent classification** based on simple NLP rules or a lightweight framework like **Rasa NLU**, **Dialogflow**, or a hand-coded decision tree.
- When the backend receives a message:
  - It tokenizes and parses the message.
  - Performs **fuzzy intent matching** using keyword-based or vector similarity scoring.
  - If the intent matches "privacy-policy", the backend responds with a trigger message like:
    ```
    Our privacy policy can be viewed at...
    ```
  - This activates a frontend hook that automatically changes the route.

---

## 🔁 Real Chat Input Examples (Payloads)
Try inputting:

- `Can I take a look at your privacy policy?`
- `What data do you collect about me?`
- `How do you store user information?`
- `Show me your privacy terms.`
- `Where can I find your privacy settings?`

These should trigger the intent if tokenized and matched against the model.

---

## 🧠 Why This Works (Strategy Behind It)

- Juice Shop challenge uses a **semantic trigger** rather than a hard-coded command.
- This means traditional command injection won’t work. Instead, you must reverse-engineer the likely **training phrases** that were used for the "privacy-policy" intent.
- This attack demonstrates **how weakly defined NLP intents can be abused** by crafting appropriate language.

---

## 🧪 How to Validate Success
You should expect the following once a correct phrase is detected:

1. The chatbot responds with a confirmation about the Privacy Policy.
2. The frontend automatically redirects to the hidden route:  
/#/privacy-security/privacy-policy

css
Copy
Edit
3. A toast notification appears:  
Privacy Policy loaded

yaml
Copy
Edit
4. The challenge is marked as **solved** in the scoreboard.

---

## 🛡️ Defense Insight
This type of attack highlights the need for:
- Strong NLP input sanitization.
- Explicit intent verification.
- Logging suspicious input patterns that hit sensitive routes.

---

## ⚙️ Terminal? Automation?
This method is purely based on human-like phrasing. It **cannot be automated via terminal** alone since it relies on the bot’s dynamic NLP processing.

For automation, a **headless browser** (e.g., Puppeteer, Selenium) would be needed to send simulated chat messages and parse DOM changes.

---

## ✅ Summary
This is a classic case of **semantic fuzzing** against weak intent classification. You don’t explo
