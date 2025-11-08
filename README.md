# V.E.C.T.O.R
Rider Telemetry System

A mobile telemetry app that records rider data using an ESP32 IMU sensor and GPS input to detect whether the user is walking, riding a scooty, or a bike.
Built with React Native (Expo), it visualizes live stats, posture, and path while storing data locally.

🚴 How It Works

IMU-based posture detection:
Uses accelerometer and gyroscope readings to calculate pitch angle.

Walk → low speed & irregular motion

Scooty → upright (pitch ~0–10°)

Bike → forward lean (pitch ~30–45°)

GPS integration:
A second phone (MIT App / GPS2IP) sends latitude & longitude every second to a local Node.js API.
The app fetches coordinates and displays position on a live map.

💾 Data Handling

Stores live sensor + GPS data every second

Keeps 1000 recent entries (100 per page)

Auto-exports to CSV after every 1000 samples

CSV columns:

timestamp,speed,accX,accY,accZ,gyroX,gyroY,gyroZ,pitch,battery,mode,lat,lon

▶️ Quick Start
git clone <repo>
cd rider-telemetry-mobile
npm install
node gps_server.js      # if using 2nd phone GPS
npm start               # run app via Expo Go


To build APK:

npm install -g eas-cli
eas build -p android --profile preview

🌟 Key Features

Real-time detection of walk/scooty/bike

Live map tracking via local GPS feed

Automatic CSV exports

Works fully offline
