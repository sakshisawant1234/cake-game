# 🏃 3D Temple Run — Flask + Three.js + Bootstrap

A browser-based endless runner inspired by Temple Run, built with **Flask**, **Three.js**, and **Bootstrap 5**. All game logic runs client-side in internal JavaScript — Flask only serves the page.

![Tech Stack](https://img.shields.io/badge/Flask-Python-black) ![Three.js](https://img.shields.io/badge/Three.js-r128-blue) ![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.3-purple)

---

## 📁 Project Structure

```
session2/
├── app.py
└── templates/
    └── index.html
```

---

## ✨ Features

- **Endless procedural track** — floor segments and side walls scroll and recycle infinitely
- **3-lane running** — switch left/right to dodge obstacles
- **Jump & slide mechanics** — jump over waist-height barriers, slide under overhead beams
- **Coin collection** — spinning coins add bonus score
- **Progressive difficulty** — speed increases and obstacles spawn faster over time
- **Bootstrap HUD** — live score, coin count, and speed multiplier via badges
- **Keyboard + on-screen controls** — playable with arrow keys, WASD, or buttons (touch/mouse friendly)
- **Win/lose alerts** — game-over and start prompts using Bootstrap alerts
- **Zero custom CSS** — 100% Bootstrap utility/component classes (only the canvas container height is inline, which Three.js requires)

---

## 🧰 Tech Stack

| Layer        | Technology                          |
|--------------|--------------------------------------|
| Backend      | Flask (Python)                       |
| 3D Rendering | Three.js r128 (CDN)                  |
| UI/Styling   | Bootstrap 5.3.3 (CDN)                |
| Game Logic   | Internal vanilla JavaScript          |

No build tools, no npm, no database — a single Flask route rendering a single self-contained HTML template.

---

## 🚀 Getting Started

### Prerequisites
- Python 3.7+
- pip

### Installation & Run

```bash
# Clone or copy the project
cd session2

# Install Flask
pip install flask

# Run the app
python app.py
```

Then open your browser to:

```
http://127.0.0.1:5000/
```

Click **Start Run** to begin playing.

---

## 🎮 Controls

| Action        | Keyboard              | On-screen Button |
|---------------|------------------------|-------------------|
| Move Left     | `←` or `A`             | ⬅ Left           |
| Move Right    | `→` or `D`             | Right ➡          |
| Jump          | `↑` or `W`             | ⬆ Jump           |
| Slide         | `↓` or `S`             | ⬇ Slide          |

**Goal:** Run as far as possible, dodge barriers and beams, and collect gold coins. Hitting an obstacle ends the run.

---

## 🏗️ How It Works

- **Runner** — a `THREE.CapsuleGeometry` body + `SphereGeometry` head, fixed at a constant world Z-position while the world scrolls past it.
- **Lane switching** — `playerLane` (0–2) maps to fixed X coordinates; position smoothly lerps toward the target lane each frame.
- **Jump/slide physics** — jump applies vertical velocity with manual gravity integration; slide scales the player down on the Y-axis for a timed duration. Both are checked against obstacle type for successful dodges.
- **Infinite track** — floor segments and walls scroll toward the camera each frame and recycle once they pass behind it, simulating endless forward motion without moving the camera itself.
- **Obstacles & coins** — spawn ahead in random lanes, scroll toward the player, and are collision-checked by lane + Z-distance overlap.
- **Difficulty scaling** — speed and obstacle spawn rate increase with elapsed time.
- **HUD** — all score/coin/speed indicators and alerts are pure Bootstrap components (`badge`, `alert`, `btn`, `card`) — no custom CSS.

---

## 📜 License

Free to use and modify for learning, demos, or personal projects.
