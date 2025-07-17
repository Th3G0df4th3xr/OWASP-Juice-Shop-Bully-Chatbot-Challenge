📁 Manual-Brute-Force/TODO.md
markdown
Copy
Edit
# 🛠️ TODO - Manual Brute Force Method

## 🔍 Recon & Preparation
- [ ] Identify that the application uses Angular (SPA) with client-side routing (`/#/`)
- [ ] List known route patterns (e.g. `/about`, `/score-board`) to understand route structure
- [ ] Create a custom route wordlist based on context (e.g., `privacy-policy`, `terms`, `security`)

## 🔧 Manual Brute Force Execution
- [ ] Launch Juice Shop in browser: `http://localhost:3000`
- [ ] Open DevTools > Network > XHR/Fetch to monitor background API calls
- [ ] In the address bar, manually attempt:
http://localhost:3000/#/privacy-security/privacy-policy

markdown
Copy
Edit
- [ ] Monitor response:
- [ ] Page content loads successfully
- [ ] Toast appears: `Privacy Policy loaded`
- [ ] Console logs indicate route change

## 🧠 Optional Advanced Steps
- [ ] Try `/#/privacy`, `/#/policy`, `/#/privacy-policy`, `/#/legal` etc.
- [ ] Load AngularJS route inspector (e.g., Batarang extension) to view hidden routes
- [ ] Observe localStorage/sessionStorage for route hints

## ✅ Validation
- [ ] Capture screenshot of the Privacy Policy page
- [ ] Save console log/Network logs showing the route access
- [ ] Note down toast message and URL pattern used

## 🧾 Documentation
- [ ] Update `README.md` with:
- [ ] Route discovered
- [ ] Manual steps taken
- [ ] Screenshot and evidence of challenge solved
