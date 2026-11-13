# T Level Engineering Core — Android app

This folder is a complete Android Studio project. It wraps the study app (17 units, 340 questions,
activities, mock exams and "My results") so students can install it from Google Play.
No sign-in: each student's name and results are saved only on their own phone.

- App name: **T Level Engineering Core**
- Package name: `uk.co.rahimachowdhury.tlevelcore` (based on your own domain; it can never be changed after the first upload)
- Targets Android 16 (API 36), as Google Play requires for new apps; runs on Android 8.0 and newer
- The app page itself is `app/src/main/assets/index.html`

---

## Step 1 — Build the app (about 30 minutes the first time)

1. Install **Android Studio** (free): https://developer.android.com/studio
2. Unzip this folder. In Android Studio choose **File → Open** and select the `TLevelCore` folder.
3. Wait for the "Gradle sync" bar at the bottom to finish (the first time it downloads a lot).
   If Android Studio offers to **upgrade the Android Gradle Plugin**, accept it.
4. Test it: **Tools → Device Manager** → create a phone emulator, then press the green ▶ **Run** button.
   (Or plug in your Android phone with USB debugging on.)
5. Build the file for Google Play: **Build → Generate Signed App Bundle or APK → Android App Bundle**.
   - Choose **Create new…** to make a *key store* (a signing key). Save the `.jks` file and its passwords somewhere safe
     and backed up — you need the same key for every future update.
   - Choose **release**. Android Studio creates `app/release/app-release.aab`. That is the file you upload.

## Step 2 — Google Play developer account

1. Sign up at https://play.google.com/console (one-off registration fee, plus identity verification).
2. **Personal account vs organisation:** a new *personal* account must run a **closed test with at least 12 testers
   for 14 days in a row** before the app can go public. Your own students with Android phones can be those testers.
   An *organisation* account (e.g. registered by the college) does not have this rule but needs business verification.

## Step 3 — Create the app in Play Console

1. **Create app** → name "T Level Engineering Core", App, Free.
2. **Store listing** — use the text in `store/store-listing.txt` and the images in the `store` folder:
   - App icon: `icon-512.png`
   - Feature graphic: `feature-graphic-1024x500.png`
   - Phone screenshots: the six `screenshot-*.png` files
3. **Privacy policy** — Google requires a web link. Upload `store/privacy-policy.html` to GitHub Pages
   (like your Unit 2 hub) and paste its link.
4. **App content** answers:
   - Data safety: **No data collected, no data shared** (everything stays on the phone).
   - Ads: **No ads**.
   - Target audience: **16–17** and **18 and over** (T Level learners).
   - Content rating questionnaire: category **Education / Reference**; answer No to everything → rated for everyone.
   - App access: **All functionality is available without special access**.
5. **Testing → Closed testing** → create a release, upload `app-release.aab`, add your testers' Google email
   addresses, and share the opt-in link with them. After 14 days, apply for **Production**.

## Updating the app later

1. Replace `app/src/main/assets/index.html` with the new version of the study app.
2. In `app/build.gradle`, add 1 to `versionCode` (e.g. 1 → 2) and change `versionName` (e.g. '1.1').
3. Build a new signed bundle with the **same key store** and upload it as a new release.
