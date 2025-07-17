📁 NLP-Trickery/TODO.md
markdown
Copy
Edit
# ✅ TODO - NLP-Trickery Chatbot Exploit

## [ ] Understand the Bot Behavior
- [ ] Interact with the chatbot widget on Juice Shop
- [ ] Observe how it responds to different privacy-related questions

## [ ] Identify Working Phrases
- [ ] Try natural questions like:
  - [ ] "Where is your privacy policy?"
  - [ ] "Can I see the privacy terms?"
  - [ ] "Do you store user information?"
- [ ] Confirm that one of the inputs triggers a redirect to:  
      `/#/privacy-security/privacy-policy`

## [ ] Validate Challenge Completion
- [ ] Check for toast: “Privacy Policy loaded”
- [ ] Verify the challenge is marked as solved

## [ ] Document Exploited Behavior
- [ ] Record successful payloads
- [ ] Note chatbot intent-response logic
- [ ] Capture screenshot of the solved challenge

## [ ] Bonus (Optional)
- [ ] Simulate NLP fuzzing via Puppeteer for automation
