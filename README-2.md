# 🌏 TourEast — Explore Northeast India

> A Progressive Web App (PWA) for discovering tourist places, planning trips, tracking expenses, and connecting with fellow travellers across Northeast India.

---

## 📱 Live Features

| Feature | Description |
|---|---|
| 🔍 **Explore Places** | Search tourist spots using the OpenTripMap API with Wikipedia images |
| 🪣 **Bucket List** | Save places you want to visit, stored in Firebase |
| 📅 **Event Manager** | Add and manage travel events with dates and locations |
| 💬 **Community** | Share and read travel experiences in real time via Firebase |
| 💸 **Expense Tracker** | Track travel expenses per place with running totals |
| 🌤 **Weather Insights** | Live weather data for any city using OpenWeatherMap |
| 🚨 **Disaster Alerts** | View and filter active disaster alerts across India |
| 🗺 **Travel & Navigation** | Interactive maps with routing via OpenRouteService + Leaflet |
| 🤖 **TourEast Helper** | AI chatbot assistant powered by Botpress |
| 📊 **Live Dashboard** | Real-time admin dashboard showing all Firebase data |

---

## 🗂 Project Structure

```
TOUREASTAPP-MAIN/
│
├── index.html              # Login / Sign Up (Firebase Auth)
├── home.html               # Main explore page with place search
├── bucket.html             # Bucket list page
├── events.html             # Event manager page
├── community.html          # Community posts page
├── expense-tracker.html    # Expense calculator page
├── weather.html            # Weather insights page
├── alert.html              # Disaster alerts page
├── details.html            # Place detail view with hotels
├── travel.html             # Map + navigation page
├── realtime-dashboard.html # Live Firebase data dashboard
│
├── app.js                  # Core app logic (search, bucket, events)
├── details.js              # Place details + hotel fetch logic
├── travel.js               # Map, routing, navigation logic
├── script.js               # Firebase community posts logic
├── firebase-db.js          # Reusable Firebase database module
├── sw.js                   # Service Worker (PWA offline support)
│
├── styles.css              # Main stylesheet
├── style.css               # Community page styles
├── stylesdetail.css        # Details page styles
├── travel.css              # Travel/map page styles
│
└── manifest.json           # PWA manifest
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/GODSON008/TOUREASTAPP-MAIN.git
cd TOUREASTAPP-MAIN
```

### 2. Set up Firebase

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Create a new project
3. Enable **Authentication** → Email/Password
4. Enable **Realtime Database** → Start in test mode
5. Copy your `firebaseConfig` from Project Settings

### 3. Add your Firebase config

Replace the config in these files with your own Firebase project values:

**`index.html`** — around line 163:
```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.firebasestorage.app",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

**`script.js`** — replace config + database URL:
```js
const databaseURL = "YOUR_DATABASE_URL";
```

**`firebase-db.js`** — replace config + DATABASE_URL constant

**`realtime-dashboard.html`** — replace config + DB_URL constant

### 4. Add your API keys

| File | Key to replace | Where to get it |
|---|---|---|
| `app.js` | `tripKey` | [OpenTripMap](https://opentripmap.io) |
| `app.js` | `UNSPLASH_KEY` | [Unsplash Developers](https://unsplash.com/developers) |
| `travel.js` | `orsKey` | [OpenRouteService](https://openrouteservice.org) |
| `weather.html` | `apiKey` | [OpenWeatherMap](https://openweathermap.org/api) |

### 5. Open the app

Open `index.html` in your browser or use a local server:

```bash
# Using VS Code Live Server extension
# Right click index.html → Open with Live Server

# Or using Python
python -m http.server 8000
# Then open http://localhost:8000
```

---

## 🔧 Tech Stack

| Technology | Purpose |
|---|---|
| HTML / CSS / JavaScript | Frontend (vanilla, no framework) |
| Firebase Authentication | User login and signup |
| Firebase Realtime Database | Live data sync across all users |
| OpenTripMap API | Tourist place search and discovery |
| Wikipedia API | Place images and descriptions |
| Unsplash API | Fallback images for places |
| OpenWeatherMap API | Live weather data |
| OpenRouteService API | Route calculation and directions |
| Leaflet.js | Interactive maps |
| Botpress | AI chatbot assistant |
| Service Worker | PWA offline support |

---

## 📸 Pages Overview

### 🏠 Home — Explore Places
Search any location to discover nearby tourist spots. Each card shows the place name, category, and image. Click a card to view full details.

### 🪣 Bucket List
Save interesting places to your personal bucket list. Data is stored in Firebase and syncs across devices.

### 📅 Event Manager
Plan your trips by adding events with a title, place, and date. All events are stored in Firebase Realtime Database.

### 💬 Community
Share your travel experiences and read posts from other travellers. Posts appear in real time thanks to Firebase.

### 💸 Expense Tracker
Add trip destinations and log individual expenses under each one. Running totals are calculated automatically.

### 🌤 Weather
Enter any city name to get current temperature, weather description, humidity, wind speed, and feels-like temperature.

### 🚨 Disaster Alerts
View active disaster alerts across India. Filter alerts by location keyword. Includes floods, cyclones, heat waves, and more.

### 🗺 Travel & Navigation
View your destination on an interactive map. Get driving/walking/cycling routes from your current location. Nearby hotels are shown with Booking.com links.

### 📊 Live Dashboard
Admin dashboard showing all Firebase data in real time — posts, bucket list, events, expenses, and alerts — with the ability to add and delete records.

---

## 📦 PWA Support

TourEast is a Progressive Web App. It can be installed on mobile and desktop devices and works partially offline thanks to the Service Worker (`sw.js`).

Files cached for offline use:
- `home.html`
- `index.html`
- `logo.png`

API responses from OpenTripMap, Wikipedia, and OpenRouteService are also cached for offline fallback.

---

## 🔒 Firebase Security Rules

For development, Realtime Database is set to test mode. Before going to production, update your rules in the Firebase console:

```json
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
```

---

## 👥 Contributing

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Commit: `git commit -m "Add your feature"`
5. Push: `git push origin feature/your-feature`
6. Open a Pull Request

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🙏 Acknowledgements

- [OpenTripMap](https://opentripmap.io) — Tourist place data
- [Wikipedia API](https://www.mediawiki.org/wiki/API:Main_page) — Place descriptions and images
- [Unsplash](https://unsplash.com) — Photography
- [OpenWeatherMap](https://openweathermap.org) — Weather data
- [OpenRouteService](https://openrouteservice.org) — Routing engine
- [Leaflet.js](https://leafletjs.com) — Maps
- [Firebase](https://firebase.google.com) — Backend and authentication
- [Botpress](https://botpress.com) — AI chatbot

---

*Built with ❤️ for Northeast India travellers*
