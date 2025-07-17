📁 Storage-Manipulation/TODO.md
markdown
Copy
Edit
# ✅ TODO – Storage Manipulation Method

## [ ] Step 1: Open the Application
- Navigate to OWASP Juice Shop in your browser.

## [ ] Step 2: Access Browser Developer Tools
- Open DevTools (`F12` or `Ctrl+Shift+I`)
- Go to the **Application** tab.

## [ ] Step 3: Inspect Storage
- Under **Storage**, go to `Local Storage` or `Session Storage`.
- Look for flags like `showPrivacyPolicy` or similar.

## [ ] Step 4: Manually Set Flag
- Inject:
  ```js
  localStorage.setItem("showPrivacyPolicy", "true");
  location.reload();
[ ] Step 5: Confirm Visibility
Check if the Privacy Policy link appears in the footer.

[ ] Step 6: Click the Link
Click on the newly visible link.

[ ] Step 7: Validate Completion
Look for a toast message: 🎉 Challenge Solved!

[ ] Optional:
Automate this step using a bookmarklet or JS snippet.
