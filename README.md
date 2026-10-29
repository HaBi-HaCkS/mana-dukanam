# Mana Dukanam: Android app

This folder is the complete Android project for the Mana Dukanam prototype. It wraps the web app in `www/index.html` (works offline, Telugu fonts included).

The app has a **Customer / Shopkeeper** switch at the top. Both roles run on the same phone with sample data, so you can show a shopkeeper the whole flow on one device. Two separate phones cannot talk to each other yet: that needs a server, which is the next build step.

## Get the APK without installing anything (about 10 minutes)

1. Make a free account at github.com and create a **new repository** (private is fine).
2. Upload everything in this folder to the repository.
   - Open the repository, choose **Add file > Upload files**, and drag in the contents of this folder.
   - The folder `.github` is hidden on some computers. If you cannot see it, turn on "show hidden files", or skip it and do step 3.
3. If `.github/workflows/build-apk.yml` did not upload: choose **Add file > Create new file**, type `.github/workflows/build-apk.yml` as the name, and paste the contents of that file from this folder.
4. Open the **Actions** tab, choose **Build Android APK** on the left, then **Run workflow**. (It also runs by itself whenever you upload files.)
5. Wait about 5 minutes for a green tick. Open the finished run and download **mana-dukanam-apk** at the bottom. Unzip it to get `app-debug.apk`.

## Install on an Android phone

1. Copy `app-debug.apk` to the phone with a USB cable or Google Drive. (WhatsApp often blocks .apk files.)
2. Tap the file. When Android asks, allow **Install unknown apps** for the app you opened it from.
3. Tap **Install**, then **Open**.

This is a debug build. It installs and runs normally and is good for showing shopkeepers and friends. Play Store needs a signed release build, which is a separate step.

## Other ways to build

- **Android Studio:** open the `android` folder, wait for Gradle to finish, then **Build > Build APK(s)**.
- **Command line** (needs JDK 21 and the Android SDK): `npm install`, then `npm run apk`. The file appears in `android/app/build/outputs/apk/debug/`.

## Changing the app

Edit `www/index.html`, then run `npx cap sync android` and build again.

## Notes

- App id: `com.manadukanam.app`. Change it in `capacitor.config.json` before you publish anywhere.
- All shops, prices and ratings are invented sample data.
- Telugu text should be checked by a native speaker before shopkeepers see it.
