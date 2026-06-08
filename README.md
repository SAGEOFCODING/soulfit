# SoulFit — Precision Health & Wellness Platform

> *Your Body. Your Data. Your Protocol.*

A personalized health web app that takes your biometric data and turns it into a complete wellness protocol — covering body composition analysis, exercise planning, Indian nutrition, meditation, and habit tracking.

---

## 🔗 Live Demo

https://sageofcode.me/

---

## 📸 Screenshots

> * <img width="1600" height="759" alt="image" src="https://github.com/user-attachments/assets/2f0ffbf4-5209-4074-bdb6-eda14dfc2b71" />
<img width="1600" height="755" alt="image" src="https://github.com/user-attachments/assets/1563556b-95e3-4117-8be6-ecb702f74cd4" />
<img width="1600" height="760" alt="image" src="https://github.com/user-attachments/assets/8f85c6e5-93da-4d94-846d-9a4ddff98638" />


*

---

## 🧠 What Is This?

Most fitness apps are generic. SoulFit is different — it asks for your actual biometrics (height, weight, waist, hip, age, symptoms) and uses them to generate a fully personalized wellness plan.

The science behind it is based on **RFM (Relative Fat Mass)** — a clinically validated metric that's significantly more accurate than BMI for estimating body fat percentage. SoulFit uses this alongside WHtR and WHR to give you a real picture of your metabolic health, then builds your plan around it.

The target audience is health-conscious individuals in India — the nutrition plans are built around Indian food culture (dal, roti, makhana, bajra, etc.) and the exercise plans account for different fitness levels from beginner to advanced.

---

## ✨ Features

### 🔐 Auth System
- Sign up / Login with local credential storage
- Session persistence across page reloads
- Per-user data isolation

### 📋 3-Step Bio Assessment
- **Step 1 — Bio Profile:** Age, gender, dietary preference, training preference (Strength / Yoga / Mixed)
- **Step 2 — Biometric Markers:** Weight, height, waist, hip, lifestyle activity level
- **Step 3 — Clinical Indicators:** 26 symptom checkboxes (fatigue, brain fog, hormonal symptoms, etc.)

### 📊 Dashboard
- **RFM Ring Chart** — animated SVG ring showing your body fat % vs healthy range
- **BMI, WHtR, WHR** — all calculated client-side from your inputs
- **Fitness Classification** — Fit / Borderline / Overweight / Obese
- **Daily Wellness Tips** — rotates 3 tips per day from a curated library
- **Motivational Quote** — changes daily
- **Sleep Tracker** — log last night's sleep hours with feedback
- **Weight Log** — track up to 7 days with an inline SVG trend chart

### 🏋️ Exercise Protocol
- Three plan types: **Strength**, **Yoga**, **Mixed**
- Full 7-day weekly schedule with rest days
- Each exercise includes:
  - Sets/reps or duration
  - Rest time
  - Difficulty level
  - Description
  - Embedded YouTube tutorial
- **Daily view** with exercise completion tracking
- **Weekly overview** grid for planning ahead
- Plan adapts based on fitness class (e.g. chair-based yoga for Obese classification)

### 🥗 Nutrition Page
- **3-Day Meal Plans** — 4 meals/day, pure vegetarian, Indian cuisine
- **FDA-style Nutrition Labels** — full macro and micronutrient breakdown per meal
- **Ingredient Lists** — expandable per recipe
- **Calorie Targets** — calculated from your TDEE (BMR × lifestyle multiplier)
- **Protein Tracker** — log protein intake in real time with goal based on bodyweight
- **Fiber Tracker** — daily fiber goal with progress bar
- **Hydration Tracker** — 8-glass visual tracker
- **Eating Window Calculator** — enter first and last meal times, get fasting window + rating

### 🧘 Meditation Timer
- Choose session duration: 5 / 10 / 15 / 20 minutes
- 5 ambient sound themes — all **synthesized in-browser** using the Web Audio API:
  - 🌧️ Rain
  - 🌊 Ocean
  - 🌿 Forest (with procedural bird chirps)
  - 🔔 Singing Bowl drone (174Hz + 528Hz harmonics)
  - 🤫 Silent
- Animated countdown ring
- Tibetan bowl sound on session start and completion
- No audio files — all audio is generated live with oscillators and noise buffers

### 💬 Health Chatbot
- Rule-based assistant covering 25+ topic categories
- Topics: RFM, BMI, exercise, yoga, nutrition, meditation, sleep, stress, hydration, Indian food, mental wellness
- Typing indicator with simulated delay for natural feel

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Framework | React 19 |
| Build Tool | Vite 8 |
| State Management | Zustand 5 |
| Animations | Framer Motion 12 |
| Icons | Lucide React |
| Audio | Web Audio API (native browser) |
| Styling | CSS Variables + Inline Styles |
| Auth / Storage | localStorage |
| Deployment | https://soulfit-steel.vercel.app/ |

No backend. No database. No external API calls. Everything runs client-side.

---

## 📁 Project Structure

```
src/
├── components/
│   ├── AssessmentForm.jsx     # 3-step onboarding form
│   ├── AuthPage.jsx           # Login / Signup split-panel
│   ├── Chatbot.jsx            # Rule-based health assistant
│   ├── FoodProtocol.jsx       # Meal plans + nutrition labels
│   ├── LandingPage.jsx        # Hero section with background video
│   ├── Navbar.jsx             # Top navigation
│   ├── SleepTracker.jsx       # Sleep logging widget
│   ├── WeeklySchedule.jsx     # Exercise protocol + YouTube embeds
│   └── WeightLog.jsx          # Weight trend chart (SVG)
├── pages/
│   ├── DashboardPage.jsx      # Main dashboard
│   ├── ExercisePage.jsx       # Exercise protocol page
│   ├── MeditationPage.jsx     # Timer + audio engine
│   └── NutritionPage.jsx      # Meal plans + trackers
├── store/
│   └── useStore.js            # Zustand store + all calculations
├── data/
│   └── plans.js               # Risk levels + therapy plan data
├── App.jsx                    # Root component + routing logic
├── main.jsx                   # Entry point
└── index.css                  # CSS variables + global styles
```

---

## 🔬 The Science Behind It

### RFM (Relative Fat Mass)
```
Male:   RFM = 64 − (20 × Height / Waist)
Female: RFM = 76 − (20 × Height / Waist)
```
RFM was introduced as a more accurate alternative to BMI because it uses **waist circumference** to estimate visceral fat — the metabolically dangerous fat around your organs — rather than just weight.

### WHtR (Waist-to-Height Ratio)
```
WHtR = Waist (cm) / Height (cm)
```
A WHtR above **0.5** indicates high visceral fat risk regardless of overall weight.

### WHR (Waist-to-Hip Ratio)
```
WHR = Waist (cm) / Hip (cm)
```
Used to determine **apple vs pear body shape** — apple shapes have higher cardiovascular risk. Thresholds: ≥0.90 for males, ≥0.80 for females.

### TDEE (Calorie Target)
```
BMR (Mifflin-St Jeor):
  Male:   (10 × weight) + (6.25 × height) − (5 × age) + 5
  Female: (10 × weight) + (6.25 × height) − (5 × age) − 161

TDEE = BMR × Activity Multiplier
  Sedentary: 1.2 | Moderate: 1.55 | Active: 1.725
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js v20.19+ or v22.12+
- npm

### Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Navigate into the project
cd YOUR_REPO_NAME

# Install dependencies
npm install

# Start the dev server
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Build for Production

```bash
npm run build
npm run preview
```

---

## 🎨 Design System

The entire UI is built on a CSS variable design system defined in `index.css`. To change the theme, edit the `:root` variables:

```css
--color-accent-primary: #22C55E;   /* Main green accent */
--color-bg-primary: #F9FAFB;       /* Page background */
--color-text-primary: #0F172A;     /* Headings */
--color-lavender: #F1F5F9;         /* Card backgrounds */
--color-border: rgba(15,23,42,0.06);
```

The design follows a **neo-brutalist light** aesthetic — clean whites and greens, bold typography, subtle box shadows, and thick borders on interactive elements.

---

## 🔮 Roadmap / Potential Improvements

- [ ] Backend integration (Node.js + PostgreSQL) for persistent data
- [ ] Dark mode toggle
- [ ] AI-powered chatbot using the Claude API (currently rule-based)
- [ ] Progress photos and measurements history
- [ ] Non-vegetarian meal plan support
- [ ] PDF export of your health report
- [ ] Push notifications for meal and exercise reminders
- [ ] Blood test marker integration (HbA1c, Vitamin D, etc.)
- [ ] Mobile app (React Native port)

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

```bash
# Create a feature branch
git checkout -b feature/your-feature-name

# Commit your changes
git commit -m "feat: add your feature description"

# Push to the branch
git push origin feature/your-feature-name

# Open a Pull Request
```

---

## 📄 License

[MIT](LICENSE)

---

## 👤 Author

**Pranav**
- GitHub: [@SAGEOFCODING](https://github.com/SAGEOFCODING)

---

> *"What seems impossible today will one day become your warm-up."*
