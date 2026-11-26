# MDCAT Prime — Android App

Capacitor wrapper around the MDCAT Prime student web app
(live site: https://studyhub-modern-live.vercel.app/,
source repo: aslamsamejo9192-lgtm/studyhub-modern-live).

- App ID: `com.mdcatprime.app`
- Version: 1.0.0 (versionCode 1)
- Web files in `www/` are a copy of the live web app (index.html, sw.js,
  manifest.json, icons). Firebase runs through the web JS SDK, so no
  `google-services.json` is needed.
- Sign-in is email/password only.

## Building the signed APK

Pushes to `main` (or a manual dispatch) run
`.github/workflows/build-apk.yml`, which builds a signed release APK
(`app-release.apk`) with GitHub Actions.

Release signing uses a dedicated keystore (alias `mdcatprime`, created
2026-11-26, valid until 2054). The keystore and its passwords live ONLY as
GitHub Actions secrets (`KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`,
`KEY_PASSWORD`) plus a local backup copy that is never committed.
The same keystore must sign every future build, or Android will refuse
updates to the installed app.
