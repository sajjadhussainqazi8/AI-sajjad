# AI Assistant (Android) — Setup Guide

## 📱 SIRF MOBILE SE APK BANANA (Computer Ke Baghair)

Ye project GitHub Actions use karta hai — matlab APK aapke phone par nahi,
**GitHub ke cloud server par** banega. Aapko sirf upload karna hai, download
APK mil jayega. Poora kaam browser (Chrome) se ho jayega.

### Step 1: GitHub Account Banayein
1. Phone browser mein jayein: https://github.com/signup
2. Free account bana lein (email + password)

### Step 2: Naya Repository Banayein
1. GitHub par login ke baad, upar right corner "+" icon dabayein → "New repository"
2. Naam dein: `AIAssistant`
3. "Public" select karein → "Create repository" dabayein

### Step 3: Ye Poori Zip File Upload Karein
1. Apne phone mein ye di gayi `AIAssistant.zip` file download karein
2. Kisi File Manager app se ise **extract/unzip** karein (Android ke built-in
   Files app ya "ZArchiver" jaisi free app se ho jata hai)
3. GitHub par apni repository kholein → "Add file" → "Upload files" dabayein
4. Extract ki hui `AIAssistant` folder ke andar jitni bhi files/folders hain
   (app, .github, build.gradle, settings.gradle, gradle.properties, README.md)
   — sab select karke upload karein
   ⚠️ Zaroori: folder ke andar wali cheezein upload karni hain, poori zip nahi
5. Neeche "Commit changes" dabayein

### Step 4: Build Khud Shuru Ho Jayega
1. Repository ke andar "Actions" tab par jayein
2. Aapko "Build APK" naam ka workflow chalte hua dikhega (2-4 minute lagte hain)
3. Agar khud shuru na ho to us par tap karein → "Run workflow" → "Run workflow" dabayein

### Step 5: APK Download Karein
1. Jab build "green tick ✅" ho jaye, us workflow run par tap karein
2. Neeche "Artifacts" section mein "AIAssistant-debug-apk" milega — tap kar ke download karein
3. Ye ek `.zip` file hogi jisme APK hoga — usko extract karein
4. `app-debug.apk` file ko apne phone mein kholein → "Install" dabayein
   (Pehli baar "Unknown apps install" ki permission maangi jayegi — Allow kar dein)

Bas — App install ho jayegi, koi computer nahi chahiye tha! 🎉

---


## Ye kya karta hai
- Background me hamesha chalta hai (Foreground Service)
- Har baar boli hui baat pehle repeat karta hai ("Aapne kaha: ...")
- Phir command samajh kar kaam karta hai: call karna, WhatsApp/Camera kholna, waqt batana
- CommandHandler.kt me naye commands aasani se add ho sakte hain

## Zaroori Cheezein
1. Android Studio (latest version) — https://developer.android.com/studio
2. Ek Android phone (USB debugging on) ya emulator

## Install Karne Ka Tareeqa
1. Android Studio kholein → "Open" → is `AIAssistant` folder ko select karein
2. Gradle sync hone dein (thoda time lagega, internet chahiye hoga)
3. Apne phone ko USB se connect karein, USB Debugging on karein (Settings > Developer Options)
4. Upar "Run" (green play button) dabayein — app phone par install ho jayegi

## App Use Karna
1. App kholein → "Assistant Start Karein" dabayein
2. Permissions maangi jayengi (Microphone, Call, SMS) — sab "Allow" karein
3. Ab boliye, jaise: "call 03001234567" ya "whatsapp kholo" ya "time batao"
4. Assistant pehle aapki baat repeat karega, phir jawab dega/kaam karega

## Zaroori Baatein (Limitations)
- Android policy ki wajah se "hamesha, bina button dabaye" sunna mushkil hai — ye version
  service start hone ke baad khud-b-khud baar baar sunta rehta hai (loop), lekin
  screen band hone ya battery optimization se rukk sakta hai. Phone settings me
  is app ko "battery optimization se exempt" karna zaroori hai:
  Settings > Apps > AI Assistant > Battery > "Unrestricted"
- Speech recognition ke liye internet ya Google app installed hona zaroori hai
- Ye ek basic prototype hai — production-level "hey Google" jaisa wake-word system
  banane ke liye Picovoice Porcupine jaisi wake-word library add karni hogi

## Naye Commands Add Karna
`CommandHandler.kt` file kholein aur `when` block me naya condition add karein:
```kotlin
text.contains("gaana") -> {
    openApp("com.spotify.music")
    "Gaana chala raha hoon"
}
```

## Agla Qadam (Suggestions)
- Wake-word ("Hey Assistant") add karne ke liye Picovoice Porcupine SDK dekhein
- Accessibility Service add kar ke poora phone control (settings badalna, scroll karna) mumkin hai
- ChatGPT/Claude API call add kar ke "smart" jawab bhi diye ja sakte hain
