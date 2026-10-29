# Deen Core AI — Android APK build

This repository is a React + Vite web app. The GitHub Actions workflow now builds the
repository itself and wraps the generated `dist/` web app in an Android project using
Capacitor. It does not look for a separate ZIP file in the repository root.

## Build an APK

1. Upload/replace the repository contents with these project files, keeping the
   `.github/workflows/build-apk.yml` file.
2. In GitHub, open **Actions** → **Build Android APK** → **Run workflow**.
3. Wait for the workflow to finish successfully.
4. Open the completed workflow run and download the
   **deen-core-ai-debug-apk** artifact. Extract it to get the APK.

## Important: AI backend

The AI chat in this project calls `/api/gemini/chat`, which is implemented by
`server.ts`. A static Android APK does not run that Express server by itself.
To make AI chat work in the installed app, deploy the Node/Express backend to a
public HTTPS host and configure the app to call that backend URL, or implement a
secure server/API arrangement before release. Do not put a private Gemini API key
directly in the Android app.

This workflow is for a debug APK. A signed release APK/AAB needs a separate signing
configuration.
