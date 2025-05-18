

---

# ESP32 + DHT11 + 2 LEDs with Firebase Realtime Database and Mobile App Control

This project demonstrates how to use an ESP32 microcontroller to:

* 📡 Read temperature and humidity from a **DHT11** sensor
* 🔄 Send sensor data to **Firebase Realtime Database**
* 💡 Receive control signals from Firebase to control **2 LEDs**
* 📱 Control LEDs using a **custom Android mobile app**

---

## 🔧 Hardware Requirements

* ESP32 development board
* DHT11 sensor
* 2x LEDs + 220Ω resistors
* Jumper wires, Breadboard
* Internet-connected Wi-Fi network

---

## 📷 Wiring Diagram

| Component    | ESP32 GPIO |
| ------------ | ---------- |
| DHT11 (Data) | GPIO 4     |
| LED 1        | GPIO 5     |
| LED 2        | GPIO 19    |

---

## ☁️ Firebase Setup

1. Create a project in [Firebase Console](https://console.firebase.google.com)
2. Enable **Email/Password authentication** (Authentication → Sign-in method)
3. Go to **Realtime Database** → Create database in **test mode**
4. Copy your **API Key** and **Database URL** from **Project Settings**
5. Install required libraries in Arduino IDE:

   * Go to **Library Manager** and install:

     * `Firebase ESP Client` by Mobitz
     * `DHT sensor library` by Adafruit
     * `Adafruit Unified Sensor`

---

## 📄 Arduino Code Snippet


## 📲 Android Studio Setup

### 1. Create Android Project

* Open Android Studio → **New Project**
* Choose **Empty Activity**
* Name: `ESP32ControlApp`
* Language: **Java** or **Kotlin**

### 2. Connect Firebase to Android App

* Open **Tools > Firebase**
* Under **Realtime Database**, click "Set up Firebase Realtime Database"
* Connect to your Firebase project
* Accept changes to `build.gradle`

### 3. Dependencies (Manual if Needed)

In `app/build.gradle`:

```gradle
implementation 'com.google.firebase:firebase-database:20.3.0'
implementation 'com.google.firebase:firebase-auth:22.3.1'
```

At the bottom:

```gradle
apply plugin: 'com.google.gms.google-services'
```

In `build.gradle (Project)`:

```gradle
classpath 'com.google.gms:google-services:4.4.1'
```

---

## 🖼️ Firebase Database Structure Example

```json
{
  "sensor": {
    "temperature": 23.4,
    "humidity": 45.2
  },
  "leds": {
    "led1": true,
    "led2": false
  }
}
```

---

## ✅ Features

* Real-time monitoring of temperature & humidity on mobile app
* Remote LED control through Firebase Realtime Database
* Simple, scalable codebase for future expansion

---

## 📌 Notes

* Ensure Firebase database rules are set to public (for testing only):

```json
{
  "rules": {
    ".read": "true",
    ".write": "true"
  }
}
```

> **⚠️ Warning:** Do not use these rules in production.

---

Let me know if you'd like a sample Android Java/Kotlin UI layout or Firebase code to match!
