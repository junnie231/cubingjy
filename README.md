# cubingjy
junyeonahn's rubiks cube timer
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>내 큐브 타이머</title>
<style>
body {
  background: linear-gradient(135deg, #1f1c2c, #928dab);
  color: #f0f0f0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem 1rem;
  user-select: none;
  min-height: 100vh;
  margin: 0;
}

#timer {
  font-weight: 900;
  text-shadow:
    0 0 5px #ff4d6d,
    0 0 10px #ff4d6d,
    0 0 20px #ff4d6d,
    0 0 40px #ff4d6d;
  letter-spacing: 0.05em;
}

#timer.ready {
  color: #6eff6e;
  text-shadow:
    0 0 8px #6eff6e,
    0 0 15px #6eff6e,
    0 0 30px #6eff6e;
}

#timer.running {
  color: #ff4d6d;
  text-shadow:
    0 0 8px #ff4d6d,
    0 0 15px #ff4d6d,
    0 0 30px #ff4d6d;
}

#scramble {
  background: rgba(0,0,0,0.25);
  padding: 0.7rem 1rem;
  border-radius: 10px;
  font-weight: 700;
  font-size: 1.7rem;
  max-width: 90vw;
  text-align: center;
  margin-bottom: 1.3rem;
  box-shadow:
    0 4px 8px rgba(0,0,0,0.4),
    inset 0 0 10px rgba(255,255,255,0.15);
}

#records {
  background: rgba(0,0,0,0.35);
  padding: 1rem 1.5rem;
  border-radius: 15px;
  box-shadow:
    0 5px 15px rgba(0,0,0,0.6),
    inset 0 0 10px rgba(255,255,255,0.1);
  max-width: 600px;
  width: 100%;
}

#records h3 {
  margin-top: 0;
  text-align: center;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #ffd700;
  text-shadow: 0 0 6px #ffd700;
}

#records ul {
  max-height: 230px;
  overflow-y: auto;
  margin-top: 0.5rem;
  padding-left: 0;
}

#records li {
  background: rgba(255, 255, 255, 0.1);
  margin-bottom: 0.5rem;
  padding: 0.5rem 1rem;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  font-weight: 600;
  font-size: 1.1rem;
  color: #fff;
  box-shadow:
    0 2px 5px rgba(0,0,0,0.5);
}

#records button {
  background: #ff4d6d;
  border-radius: 8px;
  padding: 0.25rem 0.7rem;
  font-weight: 700;
  font-size: 0.9rem;
  color: #fff;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease;
  box-shadow:
    0 0 5px #ff4d6d;
}

#records button:hover {
  background: #ff1a3a;
  box-shadow:
    0 0 10px #ff1a3a,
    0 0 15px #ff1a3a;
}

button, select {
  background: linear-gradient(145deg, #303030, #3c3c3c);
  border-radius: 12px;
  border: none;
  color: #ddd;
  padding: 0.5rem 1rem;
  margin: 0.3rem 0.6rem 0.3rem 0;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  box-shadow:
    3px 3px 6px #242424,
    -3px -3px 6px #404040;
  transition: background 0.3s ease, color 0.3s ease;
}

button:hover, select:hover {
  background: linear-gradient(145deg, #444444, #555555);
  color: #fff;
  box-shadow:
    4px 4px 8px #1f1f1f,
    -4px -4px 8px #6e6e6e;
}

#stats {
  margin-top: 1.5rem;
  background: rgba(0,0,0,0.3);
  padding: 1rem 2rem;
  border-radius: 12px;
  font-weight: 700;
  font-size: 1.2rem;
  width: 320px;
  text-align: center;
  box-shadow:
    0 0 10px #6eff6e;
}

#stats div {
  margin: 0.3rem 0;
  color: #bfbfbf;
  letter-spacing: 0.03em;
}

#stats div span {
  color: #fff;
  font-weight: 900;
}

#session-controls {
  margin-top: 1rem;
  width: 320px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.4rem;
  font-weight: 700;
  font-size: 1.1rem;
  color: #eee;
  user-select: none;
}

select {
  min-width: 130px;
  user-select: auto;
}

@media (max-width: 480px) {
  #timer {
    font-size: 3.5rem;
  }
  #scramble {
    font-size: 1.2rem;
  }
  #stats {
    width: 90vw;
    font-size: 1rem;
  }
  #session-controls {
    flex-direction: column;
    gap: 0.8rem;
    width: auto;
  }
  select, button {
    min-width: auto;
    width: 100%;
  }
}


  body {
    font-family: Arial, sans-serif;
    background: #222;
    color: #eee;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem;
    user-select: none;
  }
  #timer {
    font-size: 5rem;
    margin: 1rem 0;
    transition: color 0.3s ease;
    color: #eee;
  }
  #timer.ready {
    color: #0f0; /* 초록 */
  }
  #timer.running {
    color: #f33; /* 빨강 */
  }
  #scramble {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }
  #records {
    margin-top: 2rem;
    width: 100%;
    max-width: 600px;
  }
  #records ul {
    list-style: none;
    padding: 0;
    max-height: 200px;
    overflow-y: auto;
  }
  #records li {
    background: #333;
    margin-bottom: 0.5rem;
    padding: 0.5rem 1rem;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
  }
  button {
    background: #444;
    color: #eee;
    border: none;
    padding: 0.3rem 0.8rem;
    border-radius: 5px;
    cursor: pointer;
    margin-left: 0.5rem;
  }
  button:hover {
    background: #666;
  }
  #stats {
    margin-top: 1rem;
    font-size: 1.1rem;
  }
  #session-controls {
    margin-top: 1rem;
  }
  select {
    background: #444;
    color: #eee;
    border: none;
    padding: 0.3rem 0.8rem;
    border-radius: 5px;
    margin-left: 0.5rem;
  }
</style>
</head>
<body>

<div id="scramble">스크램블: <span id="scramble-text"></span></div>
<div id="timer">0:00.00</div>

<div id="session-controls">
  세션: 
  <select id="session-select"></select>
  <button id="new-session">새 세션 만들기</button>
  <button id="delete-session">현재 세션 삭제</button>
</div>

<button id="reset-records">기록 모두 삭제 (현재 세션)</button>

<div id="records">
  <h3>기록 리스트</h3>
  <ul id="record-list"></ul>
</div>

<div id="stats">
  <div>기록 수: <span id="count">0</span></div>
  <div>평균 (전체): <span id="avg-all">-</span></div>
  <div>평균 5: <span id="avg-5">-</span></div>
  <div>평균 12: <span id="avg-12">-</span></div>
</div>

<script>
const timerDisplay = document.getElementById('timer');
const scrambleDisplay = document.getElementById('scramble-text');
const recordList = document.getElementById('record-list');
const resetRecordsBtn = document.getElementById('reset-records');

const sessionSelect = document.getElementById('session-select');
const newSessionBtn = document.getElementById('new-session');
const deleteSessionBtn = document.getElementById('delete-session');

const countDisplay = document.getElementById('count');
const avgAllDisplay = document.getElementById('avg-all');
const avg5Display = document.getElementById('avg-5');
const avg12Display = document.getElementById('avg-12');

let startTime = 0;
let elapsed = 0;
let timerInterval = null;
let running = false;
let ready = false;

let currentSession = null;
let sessions = {};  // { sessionName: [ms, ms, ...] }

function pad(num, size = 2) {
  let s = num + "";
  while (s.length < size) s = "0" + s;
  return s;
}

function formatTime(ms) {
  if (ms === null || ms === undefined) return '-';
  const totalSeconds = ms / 1000;
  const minutes = Math.floor(totalSeconds / 60);
  const seconds = (totalSeconds % 60).toFixed(2);
  return `${minutes}:${pad(seconds, 5)}`;
}

function displayTime(ms) {
  timerDisplay.textContent = formatTime(ms);
}

function startTimer() {
  if (running) return;
  startTime = Date.now() - elapsed;
  timerInterval = setInterval(() => {
    elapsed = Date.now() - startTime;
    displayTime(elapsed);
  }, 10);
  running = true;
  ready = false;
  updateTimerColor();
}

function stopTimer() {
  if (!running) return;
  clearInterval(timerInterval);
  running = false;
  saveRecord(elapsed);
  elapsed = 0;
  displayTime(0);
  generateScramble();
  updateTimerColor();
}

function resetTimer() {
  clearInterval(timerInterval);
  elapsed = 0;
  displayTime(0);
  running = false;
  ready = false;
  updateTimerColor();
}

function saveRecord(ms) {
  if (ms === 0) return;
  if (!currentSession) return;

  sessions[currentSession].push(ms);
  saveSessionsToStorage();
  renderRecords();
  renderStats();
}

function saveSessionsToStorage() {
  localStorage.setItem('cubeTimerSessions', JSON.stringify(sessions));
  localStorage.setItem('cubeTimerCurrentSession', currentSession);
}

function loadSessionsFromStorage() {
  sessions = JSON.parse(localStorage.getItem('cubeTimerSessions') || '{}');
  if (!sessions || Object.keys(sessions).length === 0) {
    sessions = { '기본 세션': [] };
  }
  currentSession = localStorage.getItem('cubeTimerCurrentSession') || Object.keys(sessions)[0];
}

function renderSessionOptions() {
  sessionSelect.innerHTML = '';
  Object.keys(sessions).forEach(session => {
    const option = document.createElement('option');
    option.value = session;
    option.textContent = session;
    if (session === currentSession) option.selected = true;
    sessionSelect.appendChild(option);
  });
}

function renderRecords() {
  if (!currentSession) return;
  const records = sessions[currentSession] || [];
  recordList.innerHTML = '';
  records.forEach((ms, idx) => {
    const li = document.createElement('li');
    li.textContent = formatTime(ms);
    const delBtn = document.createElement('button');
    delBtn.textContent = '삭제';
    delBtn.onclick = () => {
      records.splice(idx, 1);
      saveSessionsToStorage();
      renderRecords();
      renderStats();
    };
    li.appendChild(delBtn);
    recordList.appendChild(li);
  });
}

function calculateAverage(arr) {
  if (!arr.length) return null;
  const sum = arr.reduce((a,b) => a+b, 0);
  return sum / arr.length;
}

// 평균5, 평균12는 가장 최근 5개/12개 기록 중에서 최고와 최저 제외한 나머지 평균
function calculateAvgN(arr, n) {
  if (arr.length < n) return null;
  const recent = arr.slice(-n);
  const sorted = [...recent].sort((a,b)=>a-b);
  sorted.shift(); // 최솟값 제외
  sorted.pop();   // 최댓값 제외
  const sum = sorted.reduce((a,b)=>a+b,0);
  return sum / (n - 2);
}

function renderStats() {
  if (!currentSession) return;
  const records = sessions[currentSession];
  countDisplay.textContent = records.length;
  avgAllDisplay.textContent = formatTime(calculateAverage(records));
  avg5Display.textContent = formatTime(calculateAvgN(records, 5));
  avg12Display.textContent = formatTime(calculateAvgN(records, 12));
}

function generateScramble() {
  const moves = ["R","R'","R2","L","L'","L2","U","U'","U2","D","D'","D2","F","F'","F2","B","B'","B2"];
  let scramble = [];
  let lastMove = "";
  for(let i=0; i<20; i++) {
    let move;
    do {
      move = moves[Math.floor(Math.random()*moves.length)];
    } while (move[0] === lastMove);
    scramble.push(move);
    lastMove = move[0];
  }
  scrambleDisplay.textContent = scramble.join(' ');
}

function updateTimerColor() {
  if (running) {
    timerDisplay.classList.remove('ready');
    timerDisplay.classList.add('running');
  } else if (ready) {
    timerDisplay.classList.remove('running');
    timerDisplay.classList.add('ready');
  } else {
    timerDisplay.classList.remove('running');
    timerDisplay.classList.remove('ready');
  }
}

// 이벤트

document.body.onkeydown = function(e) {
  if(e.code === 'Space' && !running && !ready) {
    // 스페이스바 눌러서 시작 준비 (초록)
    ready = true;
    updateTimerColor();
  }
}
document.body.onkeyup = function(e) {
  if(e.code === 'Space') {
    if (ready && !running) {
      // 시작
      startTimer();
    } else if (running) {
      // 멈춤
      stopTimer();
      ready = false;
      updateTimerColor();
    }
  }
}

resetRecordsBtn.onclick = () => {
  if (!currentSession) return;
  sessions[currentSession] = [];
  saveSessionsToStorage();
  renderRecords();
  renderStats();
}

sessionSelect.onchange = () => {
  currentSession = sessionSelect.value;
  saveSessionsToStorage();
  renderRecords();
  renderStats();
}

newSessionBtn.onclick = () => {
  const name = prompt('새 세션 이름을 입력하세요:');
  if (!name) return alert('세션 이름을 입력해야 합니다.');
  if (sessions[name]) return alert('이미 존재하는 세션 이름입니다.');
  sessions[name] = [];
  currentSession = name;
  saveSessionsToStorage();
  renderSessionOptions();
  renderRecords();
  renderStats();
}

deleteSessionBtn.onclick = () => {
  if (!currentSession) return;
  if (!confirm(`세션 "${currentSession}" 을(를) 삭제할까요? 기록도 모두 삭제됩니다.`)) return;
  delete sessions[currentSession];
  const keys = Object.keys(sessions);
  currentSession = keys.length ? keys[0] : null;
  saveSessionsToStorage();
  renderSessionOptions();
  renderRecords();
  renderStats();
}

// 초기화
loadSessionsFromStorage();
renderSessionOptions();
renderRecords();
renderStats();
displayTime(0);
generateScramble();
updateTimerColor();
</script>

</body>
</html>
