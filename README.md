# Candela Technologies — Network X 2026 (Vienna) meeting scheduler

A single-page site for booking meetings with Candela at Network X 2026
(VIECON, Vienna, 13–15 October 2026). Submissions are written straight
to a Google Sheet — no backend/database needed.

Files:
- `index.html` — the whole site (HTML/CSS/JS in one file)
- `apps-script.gs` — the Google Apps Script that receives form posts and writes them to a Sheet
- `README.md` — this file

## 1. Connect the form to a Google Sheet (~5 minutes)

1. Create a new Google Sheet, e.g. **"Network X 2026 – Meeting Requests"**.
2. In the Sheet, go to **Extensions → Apps Script**.
3. Delete the placeholder code and paste in the contents of `apps-script.gs`.
4. Click **Deploy → New deployment**.
   - Type: **Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Click **Deploy**, then click through Google's permission prompts (it'll warn you it's an unverified app — that's expected for a personal script; click **Advanced → Go to project (unsafe) → Allow**).
6. Copy the **Web app URL** it gives you (ends in `/exec`).
7. Open `index.html`, find this line near the bottom:
   ```js
   var SCRIPT_URL = "REPLACE_WITH_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL";
   ```
   and paste your URL in between the quotes.

Every submission will now append a row to the first tab of the sheet, with
a header row created automatically. You can add things like a "Status"
column, conditional formatting, or a Zapier/Sheets-to-Slack notification
on top of this without touching the site.

**Note:** if you ever edit and re-deploy the Apps Script, choose
**"New deployment"** again (or manage existing deployments) — editing
the code alone doesn't update a live `/exec` URL.

## 2. Fill in the Script URL

- **SCRIPT_URL** — from step 1 above.

