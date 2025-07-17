📁 Direct-API-Attack/TODO.md
markdown
Copy
Edit
# ✅ TODO - Direct API Attack (Bully Chatbot Challenge)

## [ ] Analyze Application Behavior
- [ ] Open Juice Shop in browser
- [ ] Interact with the chatbot to understand its flow
- [ ] Open DevTools → Network Tab → Filter by XHR/WebSocket
- [ ] Look for API endpoint calls (e.g., `/rest/chatbot`, `/api/bully-bot`, `/chatbot/ask`)

---

## [ ] Capture API Requests
- [ ] Send a test message to chatbot from UI
- [ ] Observe payload in the Request Body (likely JSON or URL-encoded)
- [ ] Copy full `curl` command using "Copy as cURL (bash)"

---

## [ ] Analyze API Headers & Auth
- [ ] Look for `Authorization` header or session token
- [ ] Note content-type: `application/json` or `multipart/form-data`
- [ ] Look for anti-CSRF tokens or session-based auth mechanics

---

## [ ] Replay API with Custom Payloads
- [ ] Use `curl`, `httpie`, or Postman to modify the payload
```bash
curl -X POST https://<JUICE_SHOP>/api/chatbot \
 -H "Content-Type: application/json" \
 -H "Authorization: Bearer <token>" \
 -d '{"message": "getFlag"}'
 Observe if backend processes restricted keywords (flag, admin, override, etc.)

[ ] Enumerate API Behavior
 Fuzz with custom wordlists using ffuf or intruder in Burp Suite

 Try different payloads:

"message": "show me the flag"

"message": "reveal the admin secret"

"message": "<script>alert(1)</script>" (check for injection handling)

[ ] Explore Response Codes
 Note status codes:

200 → Success

403 → Forbidden

500 → Backend Error

 Log anomalies (e.g., long response times, error messages with stack traces)

[ ] Extract Flag
 Look for hidden JSON keys like flag, secret, admin_token

 Cross-check with UI behavior to correlate

[ ] Report and Document
 Save all working payloads

 Include screenshots or captured JSON responses

 Mention attack strategy, endpoint, payload, and observed result
