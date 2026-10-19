# Matheheld
Mathe für die Schule 
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Mathe-Held Pro (Dashboard)</title>
  <style>
    :root {
      --primary: #3498db;
      --primary-dark: #2980b9;
      --success: #2ecc71;
      --success-dark: #27ae60;
      --danger: #e74c3c;
      --warning: #f39c12;
      --bg: #f0f8ff;
      --card-bg: #ffffff;
      --text: #2c3e50;
      --gray: #7f8c8d;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--bg);
      color: var(--text);
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
      padding: 10px;
      box-sizing: border-box;
    }

    .card {
      background: var(--card-bg);
      padding: 20px;
      border-radius: 20px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.1);
      text-align: center;
      max-width: 440px;
      width: 100%;
      box-sizing: border-box;
    }

    h1 {
      color: var(--primary-dark);
      margin-top: 0;
      margin-bottom: 5px;
      font-size: 1.8rem;
    }

    .score-board {
      font-size: 1.1rem;
      margin-bottom: 15px;
      color: var(--gray);
      font-weight: bold;
    }

    /* Dashboard Styles */
    .dashboard {
      display: flex;
      flex-direction: column;
      gap: 12px;
      text-align: left;
    }

    .dash-section-title {
      font-size: 1.1rem;
      font-weight: bold;
      color: var(--primary-dark);
      margin-top: 5px;
      border-bottom: 2px solid #ecf0f1;
      padding-bottom: 4px;
    }

    .mode-btn {
      width: 100%;
      padding: 14px;
      font-size: 1.1rem;
      font-weight: bold;
      background-color: var(--primary);
      color: white;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      text-align: left;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: background 0.2s, transform 0.1s;
    }

    .mode-btn:hover {
      background-color: var(--primary-dark);
      transform: scale(1.01);
    }

    .mode-btn.special {
      background-color: var(--warning);
    }
    .mode-btn.special:hover {
      background-color: #d35400;
    }

    .stats-box {
      background: #f8f9fa;
      border-radius: 12px;
      padding: 12px;
      font-size: 0.95rem;
      color: var(--text);
      text-align: left;
      border-left: 5px solid var(--primary);
    }

    .badge {
      display: inline-block;
      background-color: var(--warning);
      color: white;
      padding: 4px 12px;
      border-radius: 12px;
      font-size: 0.85rem;
      margin-bottom: 10px;
      font-weight: bold;
    }

    .task {
      font-size: 2.5rem;
      font-weight: bold;
      color: var(--primary-dark);
      margin: 15px 0;
    }

    .options-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      margin-top: 15px;
    }

    .option-btn {
      padding: 15px;
      font-size: 1.4rem;
      font-weight: bold;
      background-color: var(--primary);
      color: white;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
    }

    .option-btn:hover {
      background-color: var(--primary-dark);
      transform: scale(1.02);
    }
    .option-btn.correct { background-color: var(--success) !important; }
    .option-btn.wrong { background-color: var(--danger) !important; }

    /* Pyramiden-Design */
    .pyramid-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5px;
      margin: 10px 0;
    }
    .pyramid-row {
      display: flex;
      gap: 5px;
      justify-content: center;
    }
    .pyramid-cell {
      width: 48px;
      height: 38px;
      font-size: 1.1rem;
      font-weight: bold;
      text-align: center;
      border: 3px solid var(--primary);
      border-radius: 8px;
      box-sizing: border-box;
    }
    .pyramid-cell.fixed {
      background-color: #ecf0f1;
      color: var(--text);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .pyramid-cell.input {
      background-color: #fff;
      color: var(--primary-dark);
      outline: none;
    }
    .pyramid-cell.input:focus { border-color: var(--warning); }
    .pyramid-cell.correct { border-color: var(--success); background-color: #e8f8f5; }
    .pyramid-cell.wrong { border-color: var(--danger); background-color: #fadbd8; }
    .pyramid-cell.revealed { border-color: var(--warning); background-color: #fef9e7; color: #d35400; }

    .btn-group {
      display: flex;
      gap: 8px;
      justify-content: center;
      margin-top: 10px;
    }

    .action-btn {
      padding: 10px 15px;
      font-size: 0.95rem;
      font-weight: bold;
      color: white;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
    .check-btn { background-color: var(--success); }
    .check-btn:hover { background-color: var(--success-dark); }
    .show-solution-btn { background-color: var(--warning); }
    .show-solution-btn:hover { background-color: #d35400; }
    .back-btn { background-color: var(--gray); font-size: 0.85rem; padding: 6px 12px; margin-bottom: 10px;}
    .back-btn:hover { background-color: #555; }

    .feedback {
      margin-top: 10px;
      font-size: 1.1rem;
      font-weight: bold;
      min-height: 30px;
    }
    .correct-text { color: var(--success); }
    .wrong-text { color: var(--danger); }
    .info-text { color: #e67e22; }
  </style>
</head>
<body>

<div class="card">
  <h1>Mathe-Held ⭐</h1>
  <div class="score-board">
    Sterne: <span id="score">0</span> 🌟
  </div>

  <!-- DASHBOARD BEREICH -->
  <div id="dashboard-view" class="dashboard">
    <div class="dash-section-title">Wähle dein Training:</div>
    
    <button class="mode-btn" onclick="startMode('mult')">
      <span>✖️ Einmaleins (Multiplikation)</span> ➔
    </button>
    <button class="mode-btn" onclick="startMode('plusminus')">
      <span>➕➖ Plus & Minus (gemischt)</span> ➔
    </button>
    <button class="mode-btn" onclick="startMode('compare')">
      <span>⚖️ Grösser, kleiner, =</span> ➔
    </button>
    <button class="mode-btn special" onclick="startMode('pyramid')">
      <span>🔥 Rechenpyramide (mit Timer)</span> ➔
    </button>
    <button class="mode-btn" onclick="startMode('mixed')" style="background-color: #8e44ad;">
      <span>🎲 Alles gemischt</span> ➔
    </button>

    <div class="dash-section-title">Dein Lern-Fortschritt heute:</div>
    <div class="stats-box" id="stats-container">
      Lade Statistiken...
    </div>
  </div>

  <!-- SPIEL BEREICH -->
  <div id="game-view" style="display: none;">
    <button class="action-btn back-btn" onclick="returnToDashboard()">🏠 Zurück zum Dashboard</button>
    <div id="badge-container"></div>

    <!-- Normaler Aufgabenbereich -->
    <div id="normal-task-area">
      <div class="task" id="task">?</div>
      <div class="options-grid" id="options-grid"></div>
    </div>

    <!-- Pyramiden-Bereich -->
    <div id="pyramid-task-area" style="display: none;">
      <div style="font-size: 0.85rem; color: var(--gray);" id="pyramid-timer-text">
        ⏱️ Zeit: <span id="pyramid-timer">0.0</span> Sek.
      </div>
      <div class="pyramid-container" id="pyramid-grid"></div>
      <div class="btn-group">
        <button class="action-btn check-btn" onclick="checkPyramidAnswer()">Prüfen 🚀</button>
        <button class="action-btn show-solution-btn" onclick="showPyramidSolution()">Lösung 💡</button>
      </div>
    </div>

    <div class="feedback" id="feedback"></div>
  </div>
</div>

<script>
  // Speicher-Struktur
  let appData = JSON.parse(localStorage.getItem('matheTrainerData')) || {
    score: 0,
    history: {} // Format: "YYYY-MM-DD": { stars: 0, seconds: 0 }
  };

  let currentMode = 'mixed';
  let correctAnswer = 0;
  let canClick = true;
  let currentPyramidSolution = [];
  let currentPyramidInputs = [];
  
  // Zeit-Tracking Variablen
  let sessionStartTime = Date.now();
  let backgroundTimerInterval = null;
  let pyramidStartTime = 0;
  let pyramidTimerInterval = null;

  function initApp() {
    document.getElementById('score').textContent = appData.score;
    updateStatsDisplay();
    startBackgroundTimer();
  }

  // Hintergrund-Zeitzählung für heute
  function startBackgroundTimer() {
    if (backgroundTimerInterval) clearInterval(backgroundTimerInterval);
    backgroundTimerInterval = setInterval(() => {
      let todayStr = getTodayKey();
      if (!appData.history[todayStr]) {
        appData.history[todayStr] = { stars: 0, seconds: 0 };
      }
      appData.history[todayStr].seconds += 1;
      saveData();
    }, 1000);
  }

  function getTodayKey() {
    const d = new Date();
    return d.toISOString().split('T')[0];
  }

  function addStars(count) {
    appData.score += count;
    document.getElementById('score').textContent = appData.score;
    
    let todayStr = getTodayKey();
    if (!appData.history[todayStr]) {
      appData.history[todayStr] = { stars: 0, seconds: 0 };
    }
    appData.history[todayStr].stars += count;
    saveData();
    updateStatsDisplay();
  }

  function saveData() {
    localStorage.setItem('matheTrainerData', JSON.stringify(appData));
  }

  function updateStatsDisplay() {
    let todayStr = getTodayKey();
    let todayData = appData.history[todayStr] || { stars: 0, seconds: 0 };
    let minutes = Math.floor(todayData.seconds / 60);
    let seconds = todayData.seconds % 60;
    let timeStr = minutes > 0 ? `${minutes} Min ${seconds} Sek` : `${seconds} Sek`;

    let statsHTML = `
      ⭐ Sterne heute: <b>${todayData.stars}</b><br>
      ⏱️ Übungszeit heute: <b>${timeStr}</b><br>
      🌟 Gesamt-Sterne: <b>${appData.score}</b>
    `;
    document.getElementById('stats-container').innerHTML = statsHTML;
  }

  function startMode(mode) {
    currentMode = mode;
    document.getElementById('dashboard-view').style.display = 'none';
    document.getElementById('game-view').style.display = 'block';
    generateTask();
  }

  function returnToDashboard() {
    if (pyramidTimerInterval) clearInterval(pyramidTimerInterval);
    document.getElementById('game-view').style.display = 'none';
    document.getElementById('dashboard-view').style.display = 'flex';
    updateStatsDisplay();
  }

  function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  function generateTask() {
    canClick = true;
    if (pyramidTimerInterval) clearInterval(pyramidTimerInterval);
    document.getElementById('feedback').textContent = '';
    document.getElementById('badge-container').innerHTML = '';

    let modeToPlay = currentMode;
    if (currentMode === 'mixed') {
      const modes = ['mult', 'plusminus', 'compare', 'pyramid'];
      modeToPlay = modes[getRandomInt(0, modes.length - 1)];
    }

    if (modeToPlay === 'pyramid') {
      setupPyramidTask();
    } else {
      setupNormalTask(modeToPlay);
    }
  }

  function setupNormalTask(subMode) {
    document.getElementById('normal-task-area').style.display = 'block';
    document.getElementById('pyramid-task-area').style.display = 'none';

    let num1, num2, symbol;

    if (subMode === 'mult') {
      num1 = getRandomInt(1, 10);
      num2 = getRandomInt(1, 10);
      correctAnswer = num1 * num2;
      symbol = '·';
      document.getElementById('task').textContent = `${num1} · ${num2}`;
    } 
    else if (subMode === 'plusminus') {
      if (Math.random() < 0.5) {
        // Plusrechnung
        num1 = getRandomInt(1, 30);
        num2 = getRandomInt(1, 30);
        correctAnswer = num1 + num2;
        symbol = '+';
      } else {
        // Minusrechnung
        correctAnswer = getRandomInt(1, 20);
        num2 = getRandomInt(1, 15);
        num1 = correctAnswer + num2;
        symbol = '-';
      }
      document.getElementById('task').textContent = `${num1} ${symbol} ${num2}`;
    } 
    else if (subMode === 'compare') {
      // Grösser, kleiner, = Aufgaben (z.B. 4 + 5 [?] 10)
      let valA = getRandomInt(1, 20);
      let valB = getRandomInt(1, 20);
      let opType = getRandomInt(0, 2); // 0: <, 1: >, 2: =
      
      if (opType === 0) correctAnswer = '<';
      else if (opType === 1) correctAnswer = '>';
      else {
        valB = valA; // Damit = Sinn macht
        correctAnswer = '=';
      }
      document.getElementById('task').textContent = `${valA}  ?  ${valB}`;
    }

    // Optionen generieren
    let options = [];
    if (subMode === 'compare') {
      options = ['<', '>', '='];
    } else {
      options = [correctAnswer];
      while (options.length < 4) {
        let offset = getRandomInt(-4, 4);
        let wrong = correctAnswer + offset;
        if (wrong >= 0 && !options.includes(wrong)) {
          options.push(wrong);
        }
      }
      options.sort(() => Math.random() - 0.5);
    }

    const grid = document.getElementById('options-grid');
    grid.innerHTML = '';
    options.forEach(opt => {
      const btn = document.createElement('button');
      btn.className = 'option-btn';
      btn.textContent = opt;
      btn.onclick = () => checkNormalAnswer(opt, btn);
      grid.appendChild(btn);
    });
  }

  function checkNormalAnswer(selectedAnswer, clickedBtn) {
    if (!canClick) return;
    canClick = false;

    const feedbackEl = document.getElementById('feedback');
    const allButtons = document.querySelectorAll('.option-btn');

    // Korrekt-Prüfung (auch String-Vergleich für <, >, =)
    if (selectedAnswer == correctAnswer) {
      addStars(1);
      clickedBtn.classList.add('correct');
      feedbackEl.className = 'feedback correct-text';
      feedbackEl.textContent = 'Richtig! ✔ ⭐';
      setTimeout(generateTask, 1300);
    } else {
      clickedBtn.classList.add('wrong');
      allButtons.forEach(btn => {
        if (btn.textContent == correctAnswer) {
          btn.classList.add('correct');
        }
      });
      feedbackEl.className = 'feedback wrong-text';
      feedbackEl.textContent = 'Upps, knapp daneben! 💡';
      setTimeout(generateTask, 1800);
    }
  }

  // --- RECHENPYRAMIDE MIT TIMER ---
  function setupPyramidTask() {
    document.getElementById('normal-task-area').style.display = 'none';
    document.getElementById('pyramid-task-area').style.display = 'block';

    const difficulty = getRandomInt(0, 2);
    let diffName = "LEICHT";
    let maxBaseNum = 4;

    if (difficulty === 1) { diffName = "MITTEL"; maxBaseNum = 5; }
    else if (difficulty === 2) { diffName = "KNACKIG"; maxBaseNum = 6; }

    document.getElementById('badge-container').innerHTML = 
      `<span class="badge">🔥 PYRAMIDE (${diffName}) [+3 ⭐]</span>`;

    const b1 = getRandomInt(1, maxBaseNum);
    const b2 = getRandomInt(1, maxBaseNum);
    const b3 = getRandomInt(1, maxBaseNum);
    const b4 = getRandomInt(1, maxBaseNum);

    const m1 = b1 + b2;
    const m2 = b2 + b3;
    const m3 = b3 + b4;
    const t1 = m1 + m2;
    const t2 = m2 + m3;
    const top = t1 + t2;

    currentPyramidSolution = [
      [top],
      [t1, t2],
      [m1, m2, m3],
      [b1, b2, b3, b4]
    ];

    let mask = (difficulty === 0) ? [
      [false], [false, true], [true, false, true], [true, true, true, true]
    ] : (difficulty === 1) ? [
      [false], [true, false], [false, true, false], [true, true, false, true]
    ] : [
      [false], [true, true], [false, false, false], [true, true, true, true]
    ];

    const pyramidGrid = document.getElementById('pyramid-grid');
    pyramidGrid.innerHTML = '';
    currentPyramidInputs = [];

    currentPyramidSolution.forEach((row, rIdx) => {
      const rowDiv = document.createElement('div');
      rowDiv.className = 'pyramid-row';
      row.forEach((val, cIdx) => {
        if (mask[rIdx][cIdx]) {
          const cell = document.createElement('div');
          cell.className = 'pyramid-cell fixed';
          cell.textContent = val;
          rowDiv.appendChild(cell);
        } else {
          const input = document.createElement('input');
          input.type = 'number';
          input.className = 'pyramid-cell input';
          input.dataset.row = rIdx;
          input.dataset.col = cIdx;
          rowDiv.appendChild(input);
          currentPyramidInputs.push(input);
        }
      });
      pyramidGrid.appendChild(rowDiv);
    });

    // Timer starten
    pyramidStartTime = Date.now();
    let timerEl = document.getElementById('pyramid-timer');
    pyramidTimerInterval = setInterval(() => {
      let elapsed = ((Date.now() - pyramidStartTime) / 1000).toFixed(1);
      timerEl.textContent = elapsed;
    }, 100);
  }

  function checkPyramidAnswer() {
    if (!canClick) return;

    let allCorrect = true;
    const feedbackEl = document.getElementById('feedback');

    currentPyramidInputs.forEach(input => {
      const r = parseInt(input.dataset.row);
      const c = parseInt(input.dataset.col);
      const userVal = parseInt(input.value, 10);
      const expectedVal = currentPyramidSolution[r][c];

      if (userVal === expectedVal) {
        input.classList.remove('wrong');
        input.classList.add('correct');
      } else {
        input.classList.remove('correct');
        input.classList.add('wrong');
        allCorrect = false;
      }
    });

    if (allCorrect) {
      canClick = false;
      if (pyramidTimerInterval) clearInterval(pyramidTimerInterval);
      let elapsedSecs = ((Date.now() - pyramidStartTime) / 1000).toFixed(1);

      addStars(3);
      feedbackEl.className = 'feedback correct-text';
      feedbackEl.textContent = `Super! In ${elapsedSecs} Sek. gelöst! ✔ (+3 ⭐)`;
      setTimeout(generateTask, 2500);
    } else {
      feedbackEl.className = 'feedback wrong-text';
      feedbackEl.textContent = 'Da hat sich ein Fehler eingeschlichen! 💡';
    }
  }

  function showPyramidSolution() {
    if (!canClick) return;
    canClick = false;
    if (pyramidTimerInterval) clearInterval(pyramidTimerInterval);

    const feedbackEl = document.getElementById('feedback');
    currentPyramidInputs.forEach(input => {
      const r = parseInt(input.dataset.row);
      const c = parseInt(input.dataset.col);
      input.value = currentPyramidSolution[r][c];
      input.classList.remove('correct', 'wrong');
      input.classList.add('revealed');
      input.disabled = true;
    });

    feedbackEl.className = 'feedback info-text';
    feedbackEl.textContent = 'Hier ist die Lösung! Schau sie dir an. 💡';
    setTimeout(generateTask, 3500);
  }

  // Start beim Laden
  initApp();
</script>

</body>
</html>
