# 🪢 Tug of War Scoreboard

An interactive **Tug of War Scoreboard** built using **HTML, CSS, and JavaScript** that visually represents the competition between two teams using animated bars, a movable rope ribbon, keyboard controls, and a victory celebration 🎉.

---

## 🎯 Features

- 🎚️ **Live score control** using a slider  
- ⌨️ **Keyboard support** (Left & Right arrow keys)
- 📊 **Dynamic progress bars** for both teams
- 🪢 **Movable rope ribbon** indicating the lead
- 🎉 **Confetti celebration & sound** on victory
- 🎨 Smooth gradients and clean UI

---

## 🛠️ Tech Stack

- **HTML5** – Structure  
- **CSS3** – Styling, gradients, animations  
- **JavaScript (Vanilla)** – Logic & interactivity  

---

## 🎮 How It Works

- Move the **slider** to simulate pulling strength
- Positive values → **Team B pulls right**
- Negative values → **Team A pulls left**
- When the value reaches **±100**, the winning team triggers:
  - 🎊 Confetti animation
  - 🔊 Victory sound

---

## ⌨️ Controls

| Action | Key |
|------|----|
| Pull Right | `→` Arrow |
| Pull Left | `←` Arrow |
| Fine Control | Slider |

---

## 📂 Project Structure

```bash
tug-of-war-scoreboard/
│
├── index.html   # Main HTML file (includes CSS & JS)
└── README.md    # Project documentation
