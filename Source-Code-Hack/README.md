🧠 Source-Code-Hack
📂 Read between the lines – sometimes the source code spills the truth.

🧩 Overview
This method involves exploring the frontend Angular code and Node.js backend routing to uncover hidden functionality. The goal is to find the exact route to the Privacy Policy page, which may exist but is intentionally hidden or unlinked in the UI.

🧠 Backend Insight
Juice Shop's server-side code is typically in routes/index.js or similar files.

Routes like /privacy-policy may exist but are not exposed to users via the interface.

Look for res.sendFile(...), res.render(...), or app.get(...) methods that serve static pages or HTML.

🎯 Frontend Exploration
Check app-routing.module.ts to see if a route like /privacy-policy exists.

Look for components or links that are wrapped in conditions (*ngIf, routerLink, or hidden HTML).

It might be registered but not linked anywhere in the UI.

🚀 Goal
Identify and manually visit the hidden route (e.g., /#/privacy-policy) to trigger the challenge and verify it through the toast message, DevTools console, or network logs.

📁 Files of Interest
/src/app/app-routing.module.ts

/src/app/components/*

/routes/*.js

