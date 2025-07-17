✅ Storage-Manipulation/TODO.md
markdown
Copy
Edit
# TODO - Storage Manipulation Method

## [ ] Open Browser DevTools
- [ ] Navigate to `Application` tab
- [ ] Inspect `localStorage`, `sessionStorage`, and `IndexedDB`

## [ ] Look for Relevant Keys
- [ ] Identify flags related to UI visibility, such as:
  - `showPrivacyPolicy`
  - `displayPrivacyLink`
  - `ctf-ui`
- [ ] Document any key-value pairs related to navigation or hidden features

## [ ] Inject or Modify Storage Values
- [ ] Use JavaScript console to modify:
  ```js
  localStorage.setItem("showPrivacyPolicy", "true")
 OR clear/reset conflicting keys

[ ] Reload Application
 Observe if the Privacy Policy link is now visible

 Click the link to trigger the hidden challenge flow

[ ] Confirm Success
 Ensure toast notification appears: ✅ Challenge Solved

 Take a screenshot or note the solved challenge ID

[ ] Cleanup (Optional)
 Reset the manipulated storage values

 Document successful storage manipulation steps

vbnet
Copy
Edit
