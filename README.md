# 🚀 WebView APK Builder (Capacitor)

A minimal Android WebView app built using Capacitor that loads any website URL and generates a debug APK.

Perfect for quickly converting a website into an Android app without writing native code.

---

## ✨ Features

* 🌐 Load any website inside WebView
* 📱 Generate Android APK (Debug)
* 🎨 Custom App Icon support
* 🔒 Zoom disabled (optional)
* 📲 Landscape / Portrait mode support
* ⚡ Simple & fast setup

---

## 🛠️ Tech Stack

* Capacitor
* Node.js
* Android (Gradle)

---

## 📦 Project Setup

### 1. Clone the repository

```bash
git clone https://github.com/your-username/webview-apk-builder.git
cd webview-apk-builder
```

---

### 2. Install dependencies

```bash
npm install
```

---

### 3. Add Android platform

```bash
npx cap add android
```

---

### 4. Configure your website URL

Open:

```
capacitor.config.json
```

Update:

```json
{
  "server": {
    "url": "https://yourwebsite.com",
    "cleartext": true
  }
}
```

---

### 5. Create required folder

```bash
mkdir www
```

---

## 🎨 App Icon Setup

1. Create folder:

```bash
mkdir assets
```

2. Add your icon:

```
assets/icon.png
```

**Requirements:**

* 1024x1024
* PNG format

3. Generate icons:

```bash
npx capacitor-assets generate
```

---

## 🔄 Sync Project

```bash
npx cap sync
```

---

## 📦 Build Debug APK (CLI)

```bash
cd android
gradlew assembleDebug
```

---

## 📍 APK Location

```
android/app/build/outputs/apk/debug/app-debug.apk
```

---

## ⚙️ Optional Configurations

### Disable Zoom (Android)

Edit `MainActivity`:

```java
webView.getSettings().setSupportZoom(false);
```

---

### Force Landscape Mode

Edit:

```
android/app/src/main/AndroidManifest.xml
```

```xml
android:screenOrientation="landscape"
```

---

### Change App Name

Edit:

```
android/app/src/main/res/values/strings.xml
```

```xml
<string name="app_name">Your App Name</string>
```

---

## ⚠️ Notes

* Make sure Java (JDK 17) is installed
* Android SDK required (via Android Studio)
* `www/` folder must exist (can be empty)

---

## 🔥 Future Improvements

* Auto APK generator from URL
* Splash screen customization
* Fullscreen (kiosk mode)
* Auto print integration

---

## 📄 License

MIT License

---

## 👨‍💻 Author

Made with ❤️ by Anmol
