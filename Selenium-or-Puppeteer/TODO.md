✅ TODO - Automating Bully Chatbot using Selenium or Puppeteer
📌 Objective
Automate interactions with the Bully Chatbot using headless or visible browser automation frameworks — Selenium (Python) or Puppeteer (Node.js) — to bypass frontend validations, simulate user input, and test offensive scenarios that are difficult to perform manually.

🛠️ Pre-Requisites
Install required dependencies:

bash
Copy
Edit
pip install selenium
# or
npm install puppeteer
Ensure browser driver setup:

Selenium → ChromeDriver or GeckoDriver

Puppeteer → Headless Chromium included

🔄 Step-by-Step Tasks
Set up Environment

Clone this repository

Navigate to /Selenium-or-Puppeteer/ directory

Select Your Automation Stack

Decide between Selenium (Python) or Puppeteer (Node.js)

Prepare separate script templates:

selenium_bully_bot.py

puppeteer_bully_bot.js

Write Automation Scripts

Launch the browser

Visit the chatbot challenge page

Locate and interact with the chatbot input box

Send offensive/test payloads

Capture response messages

Check for validation, toast alerts, or DOM element changes

Handle Dynamic Elements

Implement waitForSelector() or WebDriverWait() where necessary

Monitor async loading (AJAX/XHR) or in-chat triggers

Log Outputs

Print/log chat history to local file for analysis

Record timestamps or actions for replay/research

Bonus Automation

Loop payloads from wordlist

Implement time-based fuzzing

Screenshots or video capture for PoC

⚠️ Notes
Consider using browser dev tools to inspect event listeners, network requests, and internal chat logic.

Handle captchas, rate-limiting, or anti-bot headers if they appear.

Respect ethical usage — this script is for security research within authorized environments.
