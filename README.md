# YoutubeM

Automated builds of YouTube patched with [Morphe](https://morphe.software/) — ad-free, SponsorBlock, background play, and more.

New APKs are built automatically within 24 hours of every new morphe-patches release.

---

## 📥 Download

Go to the [**Releases**](../../releases) page and download the latest:

| File | What it is |
|------|-----------|
| `YoutubeM-x.xx.xx.apk` | Patched YouTube |
| `MicroG-RE-*.apk` | Required companion (replaces Google Play Services) |

---

## ⚙️ First-time setup

Follow these steps **in order**.

### Step 1 — Allow unknown sources
On your phone: **Settings → Apps → Special app access → Install unknown apps**
Allow installs from your file manager or browser.

### Step 2 — Uninstall stock YouTube
The Play Store version of YouTube is signed by Google. Android won't let a differently-signed APK update it — you must uninstall first.

> ⚠️ You will lose your offline downloads. Watch history and subscriptions are tied to your Google account and will come back after sign-in.

### Step 3 — Install MicroG-RE
Install `MicroG-RE-*.apk` **before** YoutubeM. This replaces Google Play Services for the patched app and is the most common cause of force closes if missing.

### Step 4 — Install YoutubeM
Install `YoutubeM-x.xx.xx.apk` and open it. Sign in with your Google account when prompted.

---

## 🔄 Updating

When a new release appears, install the new `YoutubeM-*.apk` directly over the existing one — **no need to uninstall** as long as you use APKs from this repo (they share the same signing key).

Update MicroG-RE the same way if its version has changed in the release.

---

## ❓ Troubleshooting

| Problem | Fix |
|---------|-----|
| App force closes on launch | Install MicroG-RE **first**, then (re)install YoutubeM. Always use the `YoutubeM` and `MicroG-RE` APKs **from the same release** — mismatched versions can crash on launch. |
| MicroG-RE won't open / does nothing | Open it once and grant it **battery/background** permission (Settings → Apps → MicroG → Battery → Unrestricted). It runs mostly as a background service; a blank screen is normal. Make sure you installed the regular APK, not a debug build. |
| "App not installed" error | Uninstall stock YouTube from Play Store first |
| Can't sign in | Make sure MicroG-RE is installed, up to date, and allowed to run in the background |
| Missing features | Some patches only apply to specific YouTube versions — check the release notes |

---

## 🔧 What's patched

- Ad blocking
- SponsorBlock (skip sponsored segments)
- Return YouTube Dislike
- Background play (audio continues when screen is off)
- Remove tracking

Patch list is determined by [morphe-patches](https://github.com/MorpheApp/morphe-patches).

---

## 🏗️ How it works

A GitHub Actions workflow runs daily, checks for new morphe-patches releases, downloads the highest compatible YouTube version from APKPure, patches it with morphe-cli, and publishes the result here as a release.

Source: [`.github/workflows/patch-youtube.yml`](.github/workflows/patch-youtube.yml)
