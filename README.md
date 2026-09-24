# NOGADA Legal

Static site hosting Privacy Policy + Terms of Service for the NOGADA app.

Required by Apple App Store + Google Play Store as publicly-accessible URLs.

## Files

- `index.html` — landing page with links + support email
- `privacy.html` — full Privacy Policy
- `terms.html` — full Terms of Service
- `support.html` — FAQ / support page
- `subcontractor.html` — Subbie onboarding checklist, deemed-worker self check, incident steps (VIC). Ticks saved per device; Save PDF per subbie. `?lang=ko` or `?lang=en` forces the language.

All static, no build step, dark/light mode auto.

## Deploy to GitHub Pages

```sh
# 1. Go to github.com → New repository → name: "nogada-legal" → Public → Create
# 2. From this folder:
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/nogada-legal.git
git branch -M main
git push -u origin main

# 3. On github.com → repo Settings → Pages → Source: "Deploy from a branch"
#    → Branch: main / root → Save
# 4. Wait ~1 minute. Your URLs will be:
#      https://YOUR-GITHUB-USERNAME.github.io/nogada-legal/
#      https://YOUR-GITHUB-USERNAME.github.io/nogada-legal/privacy.html
#      https://YOUR-GITHUB-USERNAME.github.io/nogada-legal/terms.html
```

## Update the in-app links

Once you have the live URLs, edit `D:/claude app project/tekton-app/screens/MoreScreen.js`
and replace the placeholder constants:

```js
const PRIVACY_URL = 'https://YOUR-USERNAME.github.io/nogada-legal/privacy.html';
const TERMS_URL   = 'https://YOUR-USERNAME.github.io/nogada-legal/terms.html';
const SUBBIE_URL  = 'https://YOUR-USERNAME.github.io/nogada-legal/subcontractor.html?lang=' + i18n.language;
// More → Safety → Subbie Checklist:  Linking.openURL(SUBBIE_URL)  (or WebBrowser.openBrowserAsync)
```

Then OTA push (`eas update --branch production --message "wire legal urls"`).

## Use in App Store Connect

When filling the listing:

- **Support URL**: `https://YOUR-USERNAME.github.io/nogada-legal/`
- **Privacy Policy URL**: `https://YOUR-USERNAME.github.io/nogada-legal/privacy.html`

## Updating content later

Edit the HTML, commit, push. GitHub Pages picks up the change in ~1 minute.

```sh
git add . && git commit -m "update privacy/terms" && git push
```
