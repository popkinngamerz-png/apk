# Build OfflineHub into an Android APK (GitHub Actions)

This kit contains the supplied `offlinehub.zip` and a root-level GitHub Actions workflow. The workflow builds a **debug APK** and uploads it as an artifact; it does not publish the app to the Play Store.

## Steps

1. Sign in to GitHub and create a new repository (private is fine).
2. Extract this `offlinehub-apk-build-kit.zip` on your computer.
3. Upload **both** items to the repository root, keeping the workflow path exactly as `.github/workflows/build-apk.yml` and placing `offlinehub.zip` beside the `.github` folder. The easiest reliable method is GitHub Desktop: clone the empty repo, copy these items into the clone, commit, and push.
4. Open the repository on GitHub and select **Actions**. Open **Build OfflineHub APK**. If it has not started automatically, choose **Run workflow**.
5. Wait for the run to finish. If it fails, open the failed step and read its log; tests or Android compilation may reveal project issues that must be fixed first.
6. On a successful run, open the workflow run, find **Artifacts**, and download `OfflineHub-debug-APK`. Inside is `app-debug.apk`.
7. Transfer the APK to your Android phone and install it only if you trust the build source. Android may ask you to allow installing apps from that file manager/browser.

## Notes

- This is a **debug-signed** APK, appropriate for testing, not a Play Store release.
- The source says room chat works over the same Wi-Fi/hotspot and is not encrypted. Do not use room codes for sensitive conversations.
- This environment did not produce the APK directly: npm package downloads could not resolve `registry.npmjs.org`, and no Android SDK/Gradle installation is present here. This workflow builds it on a GitHub-hosted runner instead.
