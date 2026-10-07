# Maya Android — Build an installable APK

## Easiest method: GitHub cloud build

This project contains `.github/workflows/build-apk.yml`.

1. Create a GitHub repository.
2. Upload the **contents of this `Maya-Android` folder** to the repository.
3. Open the repository's **Actions** tab.
4. Select **Build Maya APK**.
5. Click **Run workflow**.
6. Wait for the workflow to finish.
7. Open the completed workflow run and download the **Maya-debug-apk** artifact.
8. Extract the downloaded artifact. It contains `app-debug.apk`.
9. Send `app-debug.apk` to your Android phone and tap it to install.
10. If Android asks, allow installation from that source, then install.

## Android Studio

Open the `Maya-Android` folder in Android Studio. Android Studio can sync the Gradle project and build:

`Build > Build Bundle(s) / APK(s) > Build APK(s)`

The debug APK will be under:

`app/build/outputs/apk/debug/app-debug.apk`

## Notes

- This is a debug APK and is suitable for installing/testing.
- A release APK should be signed with your own signing key before public distribution.
- The project is configured for Android API 35 and Java 17.
- The Firebase Realtime Database URL is stored in `FirebaseConfig.java`.
- The database URL alone does not bypass Firebase Security Rules. Authentication and database rules must be configured correctly before protected data can be accessed.
- The original macOS-only automation cannot be reproduced exactly on Android. Android requires user/system permissions for operations such as screen capture.
- The current AI connection is still based on the existing Ollama-compatible implementation. It does not require Ollama to be installed on the phone if you point it to a reachable server, but it is not a built-in cloud AI.
