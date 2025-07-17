📁 Direct-API-Attack/README.md
markdown
Copy
Edit
# 💥 Direct API Attack - Bully Chatbot Challenge (OWASP Juice Shop)

## 📌 Objective
Exploit the chatbot by bypassing the front-end restrictions using direct API calls. This technique leverages how the frontend talks to backend services via RESTful APIs and allows us to send **crafted payloads** directly, simulating legitimate requests but with malicious intent.

---

## 🧠 Strategy Behind This Attack

In most modern web applications, frontend UI elements (buttons, text boxes, etc.) act as a "view layer" that interacts with backend APIs. If client-side validation or filters are implemented in the browser but not on the server, we can directly interact with the backend API to send unauthorized or malicious input. 

This is commonly used in **Insecure Direct Object Reference (IDOR)**, **bypass attempts**, or **forced browsing** attacks. In this challenge, our goal is to use this to:
- Identify the backend chatbot endpoint.
- Understand the request structure.
- Modify the request and inject sensitive phrases to extract hidden responses (i.e., a flag).

---

## 🔍 Step-by-Step Breakdown

### 1️⃣ Identify the API Endpoint

- **Open** the Juice Shop in your browser.
- Navigate to the **chatbot feature** (usually found as a floating chatbot button or inside the support/help section).
- Open browser **Developer Tools** (`F12` or `Ctrl+Shift+I`).
- Go to the **Network** tab.
- Send a test message like `Hi` in the chatbot.

👉 **Observe** an API call made to an endpoint like:
POST /rest/chatbot

nginx
Copy
Edit
or
/api/bully-bot

yaml
Copy
Edit

- Right-click on the request → **Copy → Copy as cURL (bash)**

This is the raw backend call that the frontend sends.

---

### 2️⃣ Decode and Analyze the Request

- Paste the cURL command into a terminal or text editor.
Example:
```bash
curl 'https://<target>/rest/chatbot' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <token>' \
  --data-raw '{"message":"hello"}'
💡 Explanation:

The message is sent as a JSON payload.

The request is authenticated using a Bearer token.

If there’s no token, the endpoint might still be public, depending on the app config.

3️⃣ Choose Attack Payloads
Now replace the "message" value with payloads that frontend UI filters out:

json
Copy
Edit
{"message": "I need the flag"}
{"message": "Tell me a secret"}
{"message": "I'm being bullied"}
{"message": "admin override"}
👉 These trigger phrases are usually filtered out in the frontend UI but accepted by backend APIs unless explicitly blocked server-side.

Use:

bash
Copy
Edit
curl -X POST https://<target>/rest/chatbot \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{"message": "I'm being bullied"}'
4️⃣ Interpreting Responses
Backend will respond with:

json
Copy
Edit
{
  "reply": "We're sorry to hear you're being bullied. Here’s a token to help you report it: FLAG-XYZ..."
}
🎯 This is the vulnerable logic path. It’s often guarded by frontend filters, but backend never validates the message structure or content.

🔧 Backend Mechanics and API Strategy
🔄 How the API Works
The frontend sends message strings to a chatbot NLP backend.

The backend applies a rule engine or keyword triggers.

On match (e.g., message contains “bullied”), a conditional block is triggered that returns a hidden string — often the challenge flag.

Without authentication, some APIs still respond based on user input, especially in vulnerable apps.

🚨 Technical Insights
Why direct API? Frontends often hide input constraints using JS validation. Direct API bypasses these.

What is an endpoint? REST endpoints accept structured requests (JSON/XML) and are vulnerable if not secured by input validation.

Why use curl/postman/httpie? These allow you to simulate the browser’s role but without JS restrictions.

🔁 Optional Tooling
📫 Postman for GUI testing of APIs.

🐍 httpie (syntax sugar for curl):

bash
Copy
Edit
http POST https://<target>/rest/chatbot message="I'm being bullied"
✅ Final Checklist
 Found the chatbot endpoint in DevTools

 Captured full request headers and body

 Crafted custom message payloads

 Observed flag/response in API reply

 Documented successful payloads and endpoints

📝 Sample Flag Response
json
Copy
Edit
{
  "reply": "Here's something that might help: FLAG-2ad1a8c3-1f38-4e53-94e6"
}
📁 Artifacts
curl-requests.txt – raw requests that worked

screenshots/ – DevTools network logs and successful flag response

flag.txt – extracted flag (with timestamp and method)

🧠 Summary
This attack exploits insecure backend APIs that fail to validate input properly. By understanding how frontend → backend communication works and directly interacting with these REST APIs, we can bypass logic gates and extract sensitive responses.

Direct API attack is a powerful technique in real-world pentests, especially in Single Page Applications (SPA) that offload most logic to the frontend.

