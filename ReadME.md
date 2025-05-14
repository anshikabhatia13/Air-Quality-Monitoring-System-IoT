# 🌫️ ESP32-Based Air Quality Monitoring Web Server

This project implements a real-time **Air Quality Monitoring System** using an **ESP32 microcontroller**, **MQ135 gas sensor**, and **Firebase** for cloud storage and visualization. The data is displayed on a custom **web dashboard**, and optional mobile/web apps can be integrated for multi-node visualization.

---

## 📌 Features

- 📡 Real-time air quality monitoring using MQ135 sensor
- 🌡️ Optional DHT11/22 integration for temperature & humidity
- 🔄 Sends data to **Firebase Realtime Database**
- 🌍 Web dashboard with **live AQI charts** using Chart.js
- 🚨 Threshold-based alerts (client/web or buzzer)
- 🧠 Supports multiple sensor nodes via unique IDs

---

## 📦 Hardware Components

| Component         | Description                    |
|------------------|--------------------------------|
| ESP32            | Wi-Fi microcontroller board     |
| MQ135            | Air quality gas sensor          |
| DHT11 / DHT22    | (Optional) Temp & humidity sensor |
| OLED Display     | (Optional) Local AQI readout    |
| Power Supply     | USB or 5V battery               |

---

## 🛠️ Software Stack

| Tool/Library           | Purpose                                 |
|------------------------|------------------------------------------|
| Arduino IDE            | Firmware development for ESP32           |
| Firebase Realtime DB   | Cloud backend for sensor data            |
| Firebase Web Hosting   | Optional hosting for dashboard           |
| HTML + CSS + JS        | Frontend dashboard and charts            |
| Chart.js               | Live plotting of AQI trends              |
| Firebase JS SDK        | Real-time database integration           |

---

## 🔧 Setup Instructions

### 1. Circuit Diagram

- **MQ135 → ESP32**:
  - VCC → 3.3V
  - GND → GND
  - AOUT → GPIO34 (or any ADC pin)

- **DHT11 (Optional)**:
  - VCC → 3.3V
  - GND → GND
  - Data → GPIO15

### 2. Sensor Calibration

- Power MQ135 for 24–48 hours in clean air to stabilize
- Determine `Ro` value from clean air baseline
- Replace `Ro` in the code for accurate readings

### 3. Firebase Setup

- Go to [Firebase Console]
- Create a project and enable **Realtime Database**
- Set rules to test mode or add authentication
- Copy your project credentials (API key, project ID, DB URL)

### 4. Arduino Code

- Install libraries:
  - `FirebaseESP32.h`
  - `DHT.h`
  - `WiFi.h`
- Edit the `.ino` file to include:
  - Your Wi-Fi SSID/password
  - Firebase project credentials
- Upload to ESP32 using Arduino IDE

### 5. Web Dashboard (Optional)

- Host `index.html` + `script.js` on:
  - Firebase Hosting
  - GitHub Pages
  - Local web server
- Ensure Firebase JS SDK is linked
- Replace config in `script.js` with your Firebase credentials

---

## 📊 AQI Calculation

The ESP32 calculates AQI using the analog value from the MQ135 sensor:

### 6. Formula:

AQI = ((I_high - I_low)/(C_high - C_low)) * (C - C_low) + I_low
C = Measured gas concentration (ppm)
I_low, I_high = AQI breakpoints
C_low, C_high = Gas concentration breakpoints

## 7. AQI Categories:

    AQI Range	Category	Color
    0–50	Good	Green
    51–100	Moderate	Yellow
    101–150	Unhealthy for SG	Orange
    151–200	Unhealthy	Red
    201–300	Very Unhealthy	Purple
    301–500	Hazardous	Maroon

## ⚠️ Known Challenges
Challenge	Mitigation
Sensor drift	Periodic recalibration
MQ135 noise/fluctuations	Averaging and low-pass filtering
Firebase disconnection	Retry logic in code
Web latency	Use debounce + asynchronous updates
Security (Open access)	Enable Firebase Auth and rules
