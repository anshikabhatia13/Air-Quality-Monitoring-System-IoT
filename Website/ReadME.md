📄 Website README.md

markdown
Copy code
# 🌍 Air Quality Monitoring Web Dashboard

A responsive and real-time web dashboard for visualizing air quality data from IoT sensors connected via Firebase.

## 📊 Features

- Realtime air quality data: CO, CO₂, PM2.5, Temperature, Humidity, etc.
- Multi-node support (monitor multiple sensor stations)
- Firebase Realtime Database integration
- Live updating charts and gauges
- Mobile-friendly responsive design
- Hosted version embeddable in mobile apps (via WebView)

## 🚀 Live Demo

🔗 [Dashboard](https://its-rizz.github.io/IOT-PROJECT/)  


## 🛠️ Tech Stack

- HTML, CSS, JavaScript
- Chart.js or Google Charts (for visualization)
- Firebase Realtime Database
- Hosting: GitHub Pages 

## 🔧 How to Run Locally

1. Clone the repository:

   ```bash
   git clone https://github.com/anshikabhatia13/Air-Quality-Monitoring-System-IoT.git
   cd air-quality-dashboard


2. Open index.html in your browser


# No build tools required
    ```bash
    start index.html

## 📁 Folder Structure

website/
├── index.html
├── script.js
├── style.css
├── assets/
└── firebaseConfig.js (or inline in script.js)
## 📱 Companion Mobile App
This website is wrapped inside a React Native WebView and deployed as an Android mobile app. See the mobile app README for more info.