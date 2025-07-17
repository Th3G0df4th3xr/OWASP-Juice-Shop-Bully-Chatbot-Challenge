🛠️ Source-Code-Hack
📚 Overview
This method leverages access to the source code of the OWASP Juice Shop (or deployed instance) to statically analyze how and where the Privacy Policy page or endpoint is triggered. The goal is to reverse-engineer the logic and discover hidden routes, unused components, or disabled links that are still reachable.

⚔️ What We’re Doing
By reviewing the app’s backend and frontend source code, we uncover the following:

🔍 Frontend Clues (Angular)
Locate the routing config: src/app/app-routing.module.ts

Identify if there’s a hidden route like /privacy-policy that isn’t rendered in the UI

Check for conditionally hidden UI elements:
e.g.,

ts
Copy
Edit
*ngIf="!privacyPolicyHidden"
🔍 Backend Clues (Node.js)
Inspect routes/index.js or similar backend router files

Search for res.render() or res.sendFile() that serves a privacy-policy page or static asset

Look for flags, feature toggles, or unused endpoints

🧠 Why This Works
Applications often have disabled UI links but still keep backend routes alive for legacy, testing, or feature toggling. By studying the source, we eliminate guesswork and directly access hidden paths.

✅ Success Criteria
You locate and access the Privacy Policy via its hidden route or template render logic

A toast or confirmation appears in the app UI

You gain deeper understanding of client-server code split and hidden logic
