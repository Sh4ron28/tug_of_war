<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tug of War Scoreboard</title>
  <style>
    body {
      margin: 0;
      background: white;
      font-family: Arial, sans-serif;
      overflow: hidden;
    }

    .container {
      width: 100%;
      height: 50vh;
      position: relative;
      background: white;
      border-top: 2px solid #ccc;
      border-bottom: 2px solid #ccc;
    }

    .center-line {
      position: absolute;
      top: 0;
      bottom: 0;
      left: 50%;
      right: 50%
      width: 4px;
      background: black;
      z-index: 1;
    }

    .left-bar,
    .right-bar {
      position: absolute;
      top: 0;
      bottom: 0;
      z-index: 0;
    }

    .left-bar {
      right: 50%;
      background: linear-gradient(to left, red, green);
      transform-origin: right;
      height: 100%;
    }

    .right-bar {
      left: 50%;
      background: linear-gradient(to right, red, green);
      transform-origin: left;
      height: 100%;
    }

    .score-text {
      position: absolute;
      top: 10px;
      width: 100%;
      text-align: center;
      font-size: 2rem;
      z-index: 2;
      color: black;
    }

    .slider-container {
      position: absolute;
      width: 100%;
      bottom: 20px;
      text-align: center;
    }

    input[type="range"] {
      width: 80%;
    }

    .field {
      position: absolute;
      bottom: 0;
      height: 50vh;
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f5f5f5;
    }

    .rope {
      position: relative;
      width: 80%;
      height: 20px;
      background: #c58e4b;
      border-radius: 10px;
    }

    .ribbon {
      position: absolute;
      top: -10px;
      width: 10px;
      height: 40px;
      background: red;
      border-radius: 3px;
    }

    .celebration {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      pointer-events: none;
      overflow: hidden;
      display: none;
    }

    .confetti {
      position: absolute;
      width: 10px;
      height: 10px;
      background: red;
      animation: fall 3s linear infinite;
      opacity: 0.7;
    }

    @keyframes fall {
      0% {
        transform: translateY(-20px) rotate(0deg);
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
      }
    }
  </style>
</head>
<body>

<div class="container">
  <div class="score-text">Tug of War: Team A vs Team B</div>
  <div class="left-bar" id="leftBar"></div>
  <div class="right-bar" id="rightBar"></div>
  <div class="center-line"></div>
</div>

<div class="field">
  <div class="rope">
    <div class="ribbon" id="ribbon"></div>
  </div>
</div>

<div class="slider-container">
  <input type="range" min="-100" max="100" value="0" id="slider" />
</div>

<div class="celebration" id="celebration"></div>

<audio id="victorySound">
  <source src="https://www.soundjay.com/human/applause-8.mp3" type="audio/mpeg">
</audio>

<script>
  const slider = document.getElementById('slider');
  const leftBar = document.getElementById('leftBar');
  const rightBar = document.getElementById('rightBar');
  const ribbon = document.getElementById('ribbon');
  const celebration = document.getElementById('celebration');
  const sound = document.getElementById('victorySound');

  let hasCelebrated = false;

  function updateBars(value) {
    if (value > 0) {
      rightBar.style.width = (value / 100 * 50) + '%';
      leftBar.style.width = '0%';
    } else if (value < 0) {
      leftBar.style.width = (-value / 100 * 50) + '%';
      rightBar.style.width = '0%';
    } else {
      leftBar.style.width = '0%';
      rightBar.style.width = '0%';
    }

    const ribbonOffset = 40 * value / 100;
    ribbon.style.left = `calc(50% + ${ribbonOffset}%)`;

    if (Math.abs(value) === 100 && !hasCelebrated) {
      celebrate();
      hasCelebrated = true;
    } else if (Math.abs(value) < 100) {
      hasCelebrated = false;
      celebration.style.display = 'none';
    }
  }

  function celebrate() {
    sound.play();
    celebration.innerHTML = '';
    celebration.style.display = 'block';
    for (let i = 0; i < 100; i++) {
      const confetti = document.createElement('div');
      confetti.className = 'confetti';
      confetti.style.left = Math.random() * 100 + '%';
      confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 60%)`;
      confetti.style.animationDuration = (2 + Math.random() * 2) + 's';
      celebration.appendChild(confetti);
    }
    setTimeout(() => {
      celebration.style.display = 'none';
    }, 3000);
  }

  slider.addEventListener('input', () => {
    const value = parseInt(slider.value, 10);
    updateBars(value);
  });

  document.addEventListener('keydown', (e) => {
    let val = parseInt(slider.value);
    if (e.key === 'ArrowRight' && val < 100) {
      val += 5;
    } else if (e.key === 'ArrowLeft' && val > -100) {
      val -= 5;
    }
    slider.value = val;
    updateBars(val);
  });

  // Initial render
  updateBars(0);
</script>

</body>
</html>
