# ✨ Vitair
### Personal Environmental Health Intelligence — Powered by AI

> **Global Innovation Build Challenge V1 — AI Track Submission**
> Organized by Kang Chiao International School

---

## 🎯 What is Vitair?

Vitair is a real-time, AI-powered environmental health risk analyzer that combines live air quality, UV, weather, and pollution data with a user's personal health profile to generate **personalized daily health briefings** and actionable recommendations.

**Millions of people with asthma, allergies, heart conditions, and other health conditions have no easy way to understand how *their local environment* affects *them specifically* — today.** Vitair solves that.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🏥 **Health Profile** | Users input age group, health conditions (asthma, allergies, COPD, heart, diabetes, pregnancy, eczema) |
| 📍 **Live Location Detection** | GPS-based auto-detection of user location |
| 💨 **Real-Time AQI** | US Air Quality Index pulled from Open-Meteo Air Quality API |
| 🌡️ **Weather Data** | Temperature, humidity, wind, UV index from Open-Meteo |
| 🔬 **Pollutant Breakdown** | PM2.5, PM10, Ozone, NO₂, CO readings |
| 🤖 **AI Briefing** | Claude AI generates a personalized, condition-aware health briefing |
| 📅 **7-Day AQI Forecast** | Visual forecast strip showing upcoming air quality trends |
| 💡 **Smart Recommendations** | Condition-specific, actionable recommendations (masks, timing, SPF, hydration, etc.) |
| 📊 **Risk Score (0–100)** | Personalized risk score that accounts for conditions and amplifies risk for vulnerable groups |
| 📱 **Fully Responsive** | Optimized for desktop, tablet, and mobile |

---

## 🧠 How the AI Works

Vitair uses the **Claude AI API** (claude-sonnet-4) to generate a personalized health briefing based on:

1. The user's **health conditions** (e.g., asthma amplifies AQI risk by 1.4×)
2. **Real-time environmental data** from 3 free APIs
3. **Age-adjusted risk** (children and seniors get additional weighting)

The risk score algorithm:

```
Base Score = f(AQI)         # 0-90 based on AQI tier
Condition Multiplier        # Asthma/COPD: ×1.4, Heart: ×1.25, Pregnancy: ×1.2
Age Modifier               # Child/Senior: ×1.15
UV Contribution            # +5–10 points for high UV
Final Score = min(100, combined)
```

---

## 🌐 Data Sources (All Free / Open)

| API | Data | Key Required? |
|---|---|---|
| [Open-Meteo](https://open-meteo.com/) | Weather (temp, humidity, UV, wind) | ❌ No |
| [Open-Meteo Air Quality](https://air-quality-api.open-meteo.com/) | AQI, PM2.5, PM10, Ozone, NO₂, CO, 7-day forecast | ❌ No |
| [Nominatim (OSM)](https://nominatim.org/) | Reverse geocoding (location name from GPS) | ❌ No |
| [Anthropic Claude API](https://anthropic.com/) | Personalized AI health briefing | ✅ Yes (via proxy) |

> **All environmental data APIs are completely free with no key required.** This makes Vitair freely deployable by anyone.

---

## 🚀 Deployment

### Option 1: Vercel (Recommended)

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy from project root
vercel

# Done! Live in seconds.
```

### Option 2: Netlify

```bash
# Drag & drop the /vitair folder at netlify.com/drop
# OR use CLI:
npm install -g netlify-cli
netlify deploy --prod --dir .
```

### Option 3: GitHub Pages

```bash
git init
git add .
git commit -m "Initial Vitair deployment"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/vitair.git
git push -u origin main
# Enable GitHub Pages in repo Settings → Pages → Deploy from main
```

---

## 🛠️ Tech Stack

```
Frontend:     Vanilla HTML5, CSS3, JavaScript (ES2022+)
Fonts:        DM Serif Display, Syne, DM Mono (Google Fonts)
AI:           Anthropic Claude API (claude-sonnet-4)
Data:         Open-Meteo, Open-Meteo Air Quality, Nominatim
Deployment:   Vercel / Netlify / GitHub Pages (static hosting)
Version Ctrl: Git / GitHub
```

**Why vanilla JS?** Zero build step = instant deploy anywhere. No webpack, no npm install needed. Load the HTML file and it works.

---

## 📁 Project Structure

```
vitair/
├── index.html          # Complete single-page application
├── vercel.json         # Vercel deployment config
├── netlify.toml        # Netlify deployment config
├── .gitignore          # Git ignore rules
└── README.md           # This file
```

---

## 🎨 Design Philosophy

- **Dark theme** with an organic, nature-inspired green accent palette
- **DM Serif Display** for editorial authority, **Syne** for modern clarity, **DM Mono** for data labels
- Noise texture overlay for tactile depth
- Skeleton loading states and micro-interactions throughout
- Fully accessible color contrast ratios

---

## ⚖️ Ethical Considerations

- ✅ **Not a medical device** — clearly labeled as an awareness tool; no diagnoses made
- ✅ **Transparent data sources** — all sources cited in footer
- ✅ **No user data stored** — profile exists only in session memory, nothing is persisted
- ✅ **Privacy-first** — location is only used for API calls, never stored or transmitted to our servers
- ✅ **Fallback behavior** — if AI API is unavailable, a locally-generated briefing is shown

---

## 👥 Team

Built for the **Global Innovation Build Challenge V1** — AI Track
by Janhavi passionate about environmental health equity.

---

## 📄 License

MIT License — Open source, free to use and modify.
