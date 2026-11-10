# PTC AI — PTC India

An iPhone-first, installable Progressive Web App (PWA) with a premium black-and-gold interface. This is a real client-side application, not a static mockup.

## Included working modules

- **Dashboard:** live counts for saved enquiries, events, approved campaigns and today's logged spend.
- **Content Studio:** generates editable Instagram caption and Story copy from your brief; saves content ideas; previews a locally selected video.
- **Content Planner:** stores dated posts and can add a seven-day starter plan.
- **Enquiry Desk:** saves leads, tracks statuses/follow-up dates, exports leads CSV and opens a WhatsApp click-to-chat link when a number is available.
- **Events & Guestlist:** creates events, assigns a promoter and manages guest names/numbers.
- **Meta Ads desk:** creates campaign drafts, logs spend, blocks new same-day spend logs above the configured ₹300 daily limit, and gives rule-based review suggestions.
- **Backup & restore:** exports/imports the app's JSON data and deletes local data on request.
- **Offline shell:** service worker caches the app after its first successful visit.

## Important limits (transparent by design)

1. **No ad launch or spend:** PTC AI does not connect to Meta Ads API and cannot launch, pause, edit or spend on ads. “Approve draft” only marks a record approved for the user to launch manually in Meta Ads Manager. Nothing is sent to Meta.
2. **₹300 cap:** the app blocks its own new same-day spend-log entries when they would exceed the configured limit. It is not an enforcement mechanism on Meta billing. Set an account-level spending limit in Meta Ads Manager as well and verify it there.
3. **WhatsApp:** the app stores enquiries and opens a `wa.me` chat link. It does not read/sync your WhatsApp inbox or send unattended messages. Official WhatsApp Business Platform access and a secure backend are required for that.
4. **Instagram/Meta:** caption and campaign planning are local tools. Publishing, live insights and API-based optimisation are not connected.
5. **Video:** the app previews a selected local video; it does not currently encode/export a trimmed MP4. Use the iPhone Photos editor or iMovie to trim/export.
6. **Storage:** records stay in this browser's local storage on this iPhone. They do not sync between devices. Export a backup regularly. Clearing Safari website data can erase records.
7. **Privacy:** no analytics, advertising SDK, external database or secret/API token is included. Do not put access tokens or passwords into the app.

## Free deployment (GitHub Pages)

GitHub Pages can host a static PWA for free from a **public** repository. The source code in this ZIP will therefore be publicly visible if you use this method. Your actual customer records remain in your iPhone browser storage and are not uploaded to the repository.

1. On GitHub, create a new **public** repository named `ptc-ai` (sign in/create a free GitHub account if needed).
2. Upload every file and folder from this ZIP's `ptc-ai-app` directory to the repository root. Do not upload customer data or backup JSON files.
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
5. Wait for GitHub Pages to publish. Open the displayed HTTPS site URL on your iPhone in Safari.
6. In Safari, tap **Share → Add to Home Screen**. Enable **Open as Web App** if shown, then tap **Add**.
7. Launch **PTC AI** from the new Home Screen icon. Open it once while online so the offline app shell can be cached.

A static app does not need a paid server or paid app-builder subscription. GitHub Pages availability and account terms are controlled by GitHub and can change; check its current plan terms before publishing.

## Local preview for development

Serve this directory over localhost (service workers require HTTPS or localhost). For example, with Python installed:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in a browser on the same computer. For iPhone installation, use the HTTPS GitHub Pages deployment above.

## Project files

- `index.html` — app shell
- `style.css` — black-and-gold responsive design
- `app.js` — app logic and local data management
- `manifest.webmanifest` — install metadata
- `sw.js` — offline cache
- `icon-192.png`, `icon-512.png` — app icons

## Version

PTC AI v1.0 — local-first foundation, 11 November 2026.
