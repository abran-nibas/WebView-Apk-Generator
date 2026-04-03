# 🚀 WebView APK Builder (Capacitor 8)

A modern, high-performance Android WebView wrapper built with Capacitor 8.3. This project transforms any website URL into a functional Android APK with minimal configuration.

Perfect for converting progressive web apps (PWAs) or responsive websites into mobile applications without writing native code.

---

## ✨ Features

* 🌐 **Full-App WebView**: Loads any website internally (no external browser redirects).
* 📱 **Modern Tech Stack**: Powered by Capacitor 8.3 and Gradle 8.7.
* 🎨 **Native Feel**: Supports custom app icons, splash screens, and native themes.
* 🔒 **Fast & Secure**: Internal navigation allowlisting for security.
* 📲 **Adaptive Layout**: Supports both landscape and portrait modes.

---

## 🛠️ Requirements & Versions

To build this project, ensure you have the following installed:

* **Node.js**: v18 or later (LTS recommended)
* **Java SDK**: **JDK 21** (Required by Capacitor 8 / Gradle 8.7)
* **Android Studio**: Latest version with Android SDK Command-line Tools installed.
* **Capacitor**: 8.3.0

---

## 📦 Project Setup

### 1. Clone the repository

```bash
git clone https://github.com/kansalanmol-js/WebView-Apk-Generator.git
cd WebView-Apk-Generator
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure your Website URL

Open `capacitor.config.json` and set your desired website URL:

```json
{
  "appId": "com.example.webviewapp",
  "appName": "WebViewApp",
  "webDir": "www",
  "server": {
    "url": "https://yourwebsite.com",
    "cleartext": true,
    "allowNavigation": ["*"]
  }
}
```

> [!TIP]
> Setting `"allowNavigation": ["*"]` ensures that all links stay inside the app. For production, you should replace `*` with your specific domain (e.g., `["yourwebsite.com"]`).

### 4. Create Web Assets (Manual Step)

If the `www` folder or `assets` folder are missing after cloning, you must create them manually:

1. Create the `www` folder: `mkdir www`
2. Create a minimal `www/index.html` file (to prevent a blank screen on load):
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head><meta charset="UTF-8"><title>Loading...</title></head>
   <body style="background:#000;color:#fff;display:flex;justify-content:center;align-items:center;height:100vh;">
       <div>Connecting...</div>
   </body>
   </html>
   ```
3. Create the `assets` folder: `mkdir assets` (for app icons).

### 5. Synchronize with Android

This step is critical as it bridges your configuration and web assets (`www/`) to the native Android project:

```bash
npx cap sync android
```

---

## 📦 Building the APK

### 1. Fix Permissions (macOS/Linux Only)

If you are on macOS or Linux, ensure the Gradle wrapper has execution permissions:

```bash
chmod +x android/gradlew
```

### 2. Run the Build

#### On macOS / Linux:
```bash
cd android
./gradlew assembleDebug
```

#### On Windows (Command Prompt / PowerShell):
```bash
cd android
gradlew assembleDebug
```

### 3. APK Location

Once the build is successful, your APK will be located at:
`android/app/build/outputs/apk/debug/app-debug.apk`

---

## 🎨 Professional Customization

### Change App Icon
1. Place your 1024x1024 PNG icon at `assets/icon.png`.
2. Generate native assets:
   ```bash
   npx capacitor-assets generate
   ```

### Change App Name
Edit `android/app/src/main/res/values/strings.xml`:
```xml
<string name="app_name">Your Brand Name</string>
```

---

## ⚠️ Troubleshooting

### `Permission denied: ./gradlew`
Run the following command from the root directory to fix permissions:
`chmod +x android/gradlew`

### `Duplicate class kotlin.collections.jdk8...`
This issue is caused by Kotlin version mismatches. It has been fixed in this project by adding constraints to `android/app/build.gradle`. If it recurs, ensure your `kotlin-stdlib-jdk7` and `kotlin-stdlib-jdk8` are forced to version `1.8.0` or higher.

### Blank Screen on Startup
Ensure your `www/` folder contains at least an `index.html` file and that you've run `npx cap sync android` after any changes to your configuration or web assets.

---

## 👨‍💻 Author

Made with ❤️ by Anmol
