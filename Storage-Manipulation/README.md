💾 Storage-Manipulation
🧠 Hack the browser's memory, unlock hidden gems.

🧩 Overview
This method leverages browser storage features—like localStorage, sessionStorage, and IndexedDB—to expose hidden UI elements or trigger page states manually. Juice Shop sometimes stores challenge or UI toggles in these storages that can be manipulated to bypass UI restrictions.

🎯 Objective
Discover if there's a key or flag in browser storage that controls the visibility of the Privacy Policy link.

Modify or inject values directly to simulate access.

🔍 Where to Look
✅ localStorage / sessionStorage
Use browser DevTools → Application tab.

Look for keys like:

displayPrivacyLink

showHiddenPages

ctf-ui

Example:

js
Copy
Edit
localStorage.setItem("showPrivacyPolicy", true)
✅ IndexedDB
Navigate to indexedDB inside the Application tab.

Check if any values (such as feature toggles or flags) can be modified.

🔐 Backend Context
Backend might serve a static page but hide it from users. The front-end may conditionally render based on storage flags. Manipulating these values can enable previously hidden content.

🚀 Result
After setting the correct key:

Reload the page.

The Privacy Policy link might appear in the footer or nav.

Clicking it should trigger a toast message and solve the challenge.
