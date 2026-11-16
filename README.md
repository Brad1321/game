# Pokémon Showdown — Android app

Everything needed to turn the game into an installable Android app (`.apk`). The game works fully offline: all 151 Pokémon artwork files are bundled in `www/art/`.

## Easiest way to get the APK (no Android Studio needed)

1. Create a free **private** repository on github.com (e.g. `pokemon-showdown`).
2. Upload everything in this folder to it (drag and drop on the repo page; keep the `.github` folder).
3. Open the repo's **Actions** tab → **Build Android APK** → **Run workflow**. (It also runs automatically on every push.)
4. After ~5 minutes, open the finished run and download **pokemon-showdown-apk** — it contains `app-debug.apk`.
5. Send that file to your friends (AirDrop isn't for Android — use Drive, email, WhatsApp, or a USB cable).

## Installing on a phone (sideloading)

1. Open the `.apk` on the phone.
2. Android will ask to allow installs from that app (Files, Chrome, Drive…) — turn on **Allow from this source**.
3. Tap **Install**. If Play Protect warns about an unknown developer, choose **Install anyway** — it's your own app.

Every friend needs the APK on their own phone. The game is pass-the-phone: two players share one device.

## Changing the game later

- Edit `www/index.html`, push to GitHub, run the workflow again, and share the new APK. Friends install it over the old one (saved teams are kept as long as the app isn't uninstalled).

## Building on your own computer instead

Needs Node 20+, Java 21 and Android Studio (or just the Android SDK):

```
npm install
npx cap add android
npx capacitor-assets generate --android --iconBackgroundColor '#ffcb05' --iconBackgroundColorDark '#ffcb05'
npx cap sync android
cd android && ./gradlew assembleDebug
```
The APK appears at `android/app/build/outputs/apk/debug/app-debug.apk`.

## Notes

- This is a *debug-signed* APK: perfect for sharing with friends. It cannot be uploaded to the Play Store (that needs a release build with your own signing key).
- iPhone: this APK is Android-only. iPhones can instead open the game from a web link and use **Share → Add to Home Screen** if you host `www/` somewhere (e.g. GitHub Pages).
- Fan-made project. Pokémon names and artwork belong to their respective rights holders; keep it private among friends.
