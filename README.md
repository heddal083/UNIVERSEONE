<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>UNIVERSE : ONE</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;900&family=Noto+Sans+KR:wght@300;400;500;700&display=swap');

:root {
  --bg: #050609;
  --panel: #0b1119;
  --cyan: #00f0ff;
  --pink: #ff3dab;
  --white: #e9fcff;
  --muted: #657780;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background: var(--bg);
  color: var(--white);
  font-family: 'Noto Sans KR', sans-serif;
  overflow-x: hidden;
}

body::after {
  content: "";
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 20;
  opacity: .12;
  background: repeating-linear-gradient(
    transparent 0px,
    transparent 3px,
    rgba(0,240,255,.12) 4px
  );
}

button { font-family: inherit; cursor: pointer; }

/* BACKGROUND */

.bg-grid {
  position: fixed;
  inset: 0;
  pointer-events: none;
  background-image:
    linear-gradient(rgba(0,240,255,.035) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,240,255,.035) 1px, transparent 1px);
  background-size: 48px 48px;
  mask-image: linear-gradient(to bottom, black, transparent);
}

/* ENTRY SCREEN */

#entry {
  position: fixed;
  inset: 0;
  z-index: 100;
  background: #030508;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  transition: opacity 1s, visibility 1s;
}

#entry.hidden {
  opacity: 0;
  visibility: hidden;
}

.entry-content { width: 90%; max-width: 650px; }

.entry-code {
  color: var(--cyan);
  font: 11px Orbitron;
  letter-spacing: 5px;
  margin-bottom: 40px;
  animation: blink 2s infinite;
}

.logo {
  font: 900 clamp(35px, 8vw, 78px) Orbitron;
  letter-spacing: -4px;
  text-shadow: 3px 0 var(--pink), -3px 0 var(--cyan);
  animation: glitch 4s infinite;
}

.logo span { color: var(--cyan); }

.entry-sub {
  font: 11px Orbitron;
  letter-spacing: 5px;
  color: #8499a4;
  margin-top: 18px;
}

.entry-line {
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--cyan), transparent);
  margin: 45px 0;
}

#enterBtn {
  padding: 17px 45px;
  color: var(--cyan);
  border: 1px solid var(--cyan);
  background: transparent;
  letter-spacing: 4px;
  font: 13px Orbitron;
  transition: .3s;
}

#enterBtn:hover {
  background: var(--cyan);
  color: #000;
  box-shadow: 0 0 35px var(--cyan);
}

.entry-footer {
  margin-top: 50px;
  color: #52616b;
  font: 9px Orbitron;
  letter-spacing: 2px;
}

@keyframes blink {
  50% { opacity: .25; }
}

@keyframes glitch {
  0%, 92%, 100% { transform: translateX(0); }
  94% { transform: translateX(-3px); }
  96% { transform: translateX(3px); }
}

/* MAIN */

#main { display: none; min-height: 100vh; }

header {
  height: 75px;
  padding: 0 6%;
  border-bottom: 1px solid #17252e;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: sticky;
  top: 0;
  background: rgba(5,6,9,.9);
  backdrop-filter: blur(15px);
  z-index: 30;
}

.header-logo {
  font: 700 17px Orbitron;
  letter-spacing: -1px;
  cursor: pointer;
}

.header-logo span { color: var(--cyan); }

nav { display: flex; gap: 30px; }

nav button {
  background: none;
  border: none;
  color: #81919a;
  font: 11px Orbitron;
  letter-spacing: 2px;
}

nav button:hover, nav button.active {
  color: var(--cyan);
}

/* HERO */

.hero {
  min-height: 570px;
  padding: 110px 8% 90px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;
  background:
    radial-gradient(ellipse at 75% 45%, #10313b55, transparent 55%),
    linear-gradient(120deg, #050609, #0a141d, #050609);
}

.hero::after {
  content: "ONE";
  position: absolute;
  right: 3%;
  top: 20%;
  font: 900 clamp(150px, 30vw, 380px) Orbitron;
  color: rgba(0,240,255,.035);
  pointer-events: none;
}

.hero-label {
  font: 11px Orbitron;
  color: var(--cyan);
  letter-spacing: 5px;
  margin-bottom: 25px;
}

.hero h1 {
  font: 900 clamp(35px, 7vw, 85px) Orbitron;
  line-height: 1.15;
  letter-spacing: -4px;
  margin: 0;
  position: relative;
  z-index: 1;
}

.hero h1 span { color: var(--cyan); }

.hero-desc {
  color: #82949e;
  line-height: 2;
  font-size: 13px;
  margin-top: 30px;
}

.system-status {
  margin-top: 55px;
  display: flex;
  gap: 30px;
  flex-wrap: wrap;
  font: 10px Orbitron;
  color: #738892;
}

.status-dot {
  display: inline-block;
  width: 6px;
  height: 6px;
  background: var(--cyan);
  border-radius: 50%;
  margin-right: 8px;
  box-shadow: 0 0 10px var(--cyan);
}

/* SECTIONS */

.section {
  display: none;
  padding: 90px 7%;
  min-height: 75vh;
}

.section.active { display: block; }

.section-heading {
  border-left: 2px solid var(--cyan);
  padding-left: 20px;
  margin-bottom: 55px;
}

.section-heading small {
  font: 10px Orbitron;
  color: var(--cyan);
  letter-spacing: 4px;
}

.section-heading h2 {
  font: 700 clamp(27px, 5vw, 45px) Orbitron;
  margin: 12px 0;
}

.section-heading p {
  font-size: 12px;
  color: var(--muted);
}

/* FILTER */

.filters {
  display: flex;
  gap: 10px;
  margin-bottom: 35px;
}

.filter-btn {
  background: transparent;
  color: #81919a;
  border: 1px solid #263943;
  padding: 12px 22px;
  font: 10px Orbitron;
  letter-spacing: 2px;
}

.filter-btn.active {
  border-color: var(--cyan);
  color: var(--cyan);
  background: #00f0ff0d;
}

/* CARDS */

.participant-grid {
  display: grid;
  grid-template-columns: repeat(5, minmax(0, 1fr));
  gap: 18px;
}

.participant-card {
  position: relative;
  background: var(--panel);
  border: 1px solid #1c303a;
  overflow: hidden;
  cursor: pointer;
  transition: .35s;
}

.participant-card:hover {
  transform: translateY(-7px);
  border-color: var(--cyan);
  box-shadow: 0 0 25px #00f0ff20;
}

.card-image {
  width: 100%;
  aspect-ratio: 3 / 4;
  display: block;
  object-fit: cover;
  background:
    linear-gradient(145deg, #10212c, #080c12);
}

.card-image-fallback {
  width: 100%;
  aspect-ratio: 3 / 4;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #00f0ff50;
  font: 30px Orbitron;
  background:
    radial-gradient(circle, #153a45, #080d14 70%);
}

.card-info { padding: 15px; }

.card-number {
  font: 10px Orbitron;
  color: var(--cyan);
  letter-spacing: 2px;
}

.card-name {
  font-size: 16px;
  margin-top: 10px;
  font-weight: 500;
}

.card-sub {
  font: 9px Orbitron;
  color: #71828b;
  margin-top: 8px;
  letter-spacing: 1px;
}

.card-gender {
  position: absolute;
  top: 10px;
  left: 10px;
  background: #050609cc;
  padding: 6px 8px;
  font: 9px Orbitron;
  color: var(--cyan);
}

/* INFORMATION */

.info-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}

.info-box {
  padding: 35px;
  border: 1px solid #20333d;
  background: linear-gradient(135deg, #0b141d, #070a0f);
  min-height: 190px;
}

.info-box small {
  color: var(--cyan);
  font: 10px Orbitron;
  letter-spacing: 3px;
}

.info-box h3 {
  font: 18px Orbitron;
  margin: 20px 0;
}

.info-box p {
  font-size: 12px;
  color: #8799a2;
  line-height: 2;
}

/* MODAL */

#modal {
  position: fixed;
  inset: 0;
  background: #000e;
  backdrop-filter: blur(12px);
  z-index: 80;
  display: none;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.modal-content {
  width: 100%;
  max-width: 600px;
  background: #0a111a;
  border: 1px solid var(--cyan);
  padding: 30px;
  position: relative;
}

.modal-close {
  position: absolute;
  right: 20px;
  top: 15px;
  background: none;
  color: var(--cyan);
  border: none;
  font: 20px Orbitron;
}

.modal-content h2 {
  font: 25px Orbitron;
  color: var(--cyan);
}

.modal-content p {
  font-size: 12px;
  line-height: 2;
  color: #9aaeb7;
}

/* FOOTER */

footer {
  padding: 45px 7%;
  border-top: 1px solid #1c303a;
  color: #596c76;
  font: 9px Orbitron;
  letter-spacing: 2px;
  line-height: 2;
}

@media(max-width: 900px) {
  .participant-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media(max-width: 550px) {
  header { padding: 0 5%; }
  nav { gap: 13px; }
  nav button { font-size: 9px; letter-spacing: 0; }
  .hero { min-height: 500px; padding: 80px 7%; }
  .participant-grid { grid-template-columns: repeat(2, 1fr); gap: 10px; }
  .info-grid { grid-template-columns: 1fr; }
  .section { padding: 65px 5%; }
}
</style>
</head>

<body>
<div class="bg-grid"></div>

<!-- ENTRY -->
<div id="entry">
  <div class="entry-content">
    <div class="entry-code">SIGNAL DETECTED // EARTH-001</div>
    <div class="logo">UNIVERSE <span>: ONE</span></div>
    <div class="entry-sub">INTERGALACTIC IDOL SURVIVAL</div>
    <div class="entry-line"></div>
    <button id="enterBtn" onclick="enterUniverse()">
      ENTER THE UNIVERSE ↗
    </button>
    <div class="entry-footer">
      SYSTEM INITIALIZED / AWAITING YOUR ARRIVAL
    </div>
  </div>
</div>

<!-- MAIN -->
<div id="main">

<header>
  <div class="header-logo" onclick="showSection('home')">
    UNIVERSE <span>: ONE</span>
  </div>
  <nav>
    <button class="active" onclick="showSection('home',this)">HOME</button>
    <button onclick="showSection('participants',this)">PARTICIPANTS</button>
    <button onclick="showSection('information',this)">INFORMATION</button>
  </nav>
</header>

<!-- HOME -->
<section id="home" class="section active" style="padding:0">
  <div class="hero">
    <div class="hero-label">PROJECT UO-001 / TRANSMISSION LIVE</div>
    <h1>FIND YOUR<br><span>ONE.</span></h1>
    <div class="hero-desc">
      20 SIGNALS. ONE DESTINATION.<br>
      A NEW UNIVERSE IS WAITING FOR ITS STARS.<br>
      ARE YOU READY TO CHOOSE?
    </div>
    <div class="system-status">
      <div><span class="status-dot"></span>SYSTEM ONLINE</div>
      <div>20 PARTICIPANTS DETECTED</div>
      <div>EARTH CONNECTION ESTABLISHED</div>
    </div>
  </div>
</section>

<!-- PARTICIPANTS -->
<section id="participants" class="section">
  <div class="section-heading">
    <small>DATABASE // 001</small>
    <h2>PARTICIPANTS</h2>
    <p>SELECT YOUR SIGNAL. DISCOVER YOUR DESTINY.</p>
  </div>

  <div class="filters">
    <button class="filter-btn active" onclick="filterCards('ALL',this)">ALL</button>
    <button class="filter-btn" onclick="filterCards('BOYS',this)">BOYS</button>
    <button class="filter-btn" onclick="filterCards('GIRLS',this)">GIRLS</button>
  </div>

  <div class="participant-grid" id="participantGrid"></div>
</section>

<!-- INFORMATION -->
<section id="information" class="section">
  <div class="section-heading">
    <small>ARCHIVE // 002</small>
    <h2>INFORMATION</h2>
    <p>ACCESSING PROJECT DOCUMENTS...</p>
  </div>

  <div class="info-grid">
    <div class="info-box">
      <small>01 / PROJECT</small>
      <h3>WHAT IS UNIVERSE : ONE?</h3>
      <p>
        서로 다른 행성에서 모인 21명의 참가자.
        단 하나의 목표를 향해 경쟁하는
        인터갤럭틱 아이돌 서바이벌 프로젝트.
      </p>
    </div>

    <div class="info-box">
      <small>02 / SURVIVAL</small>
      <h3>THE SURVIVAL</h3>
      <p>
        참가자들은 다양한 미션을 통해 자신의 가능성을 증명한다.
        최종적으로 선택받는 단 하나의 존재는 누구인가?
      </p>
    </div>

    <div class="info-box">
      <small>03 / UNIVERSE</small>
      <h3>THE UNKNOWN WORLD</h3>
      <p>
        지구가 아닌 또 다른 세계.
        이곳에 모인 참가자들의 정체와 목적은 아직 밝혀지지 않았다.
      </p>
    </div>

    <div class="info-box">
      <small>04 / SYSTEM</small>
      <h3>CONNECTION ESTABLISHED</h3>
      <p>
        모든 기록은 시스템에 저장된다.
        당신의 선택이 이 세계의 미래를 바꿀 수도 있다.
      </p>
    </div>
  </div>
</section>

<footer>
  UNIVERSE : ONE © 2026<br>
  INTERGALACTIC IDOL SURVIVAL PROJECT<br>
  ALL SIGNALS RESERVED. / SYSTEM UO-001
</footer>

</div>

<!-- PROFILE MODAL -->
<div id="modal" onclick="closeModal(event)">
  <div class="modal-content">
    <button class="modal-close" onclick="closeModal()">×</button>
    <small id="modalNumber" style="color:var(--cyan);font-family:Orbitron"></small>
    <h2 id="modalName"></h2>
    <p id="modalDescription">
      PROFILE DATA NOT FOUND.
    </p>
  </div>
</div>

<script>

// 참가자 데이터
// 실제 이름과 설명은 추후 교체

const participants = [
  {
    id: 'B01',
    gender: 'BOYS',
    name: '참가자 이름',
    image: 'https://이미지주소.jpg',
    description: '참가자 소개'
  },
  {
    id: 'B02',
    gender: 'BOYS',
    name: '참가자 이름',
    image: 'https://이미지주소.jpg',
    description: '참가자 소개'
  },
  {
    id: 'G01',
    gender: 'GIRLS',
    name: '에피나',
    image: 'https://E791E500-EC91-45AF-82E5-A77B36358B1B.jpeg',
    description: '참가자 소개'
  }
];
  ...Array.from({length:10}, (_,i) => ({
    id: `G${String(i+1).padStart(2,'0')}`,
    gender: 'GIRLS',
    name: `GIRL SUBJECT ${String(i+1).padStart(2,'0')}`,
    image: `images/g${String(i+1).padStart(2,'0')}.jpg`,
    description: 'PROFILE DATA NOT FOUND.'
  }))
];

// ENTRY
function enterUniverse() {
  document.getElementById('entry').classList.add('hidden');
  document.getElementById('main').style.display = 'block';
}

// NAVIGATION
function showSection(id, btn) {
  document.querySelectorAll('.section').forEach(s => {
    s.classList.remove('active');
  });

  document.getElementById(id).classList.add('active');

  document.querySelectorAll('nav button').forEach(b => {
    b.classList.remove('active');
  });

  if(btn) btn.classList.add('active');

  window.scrollTo({top:0, behavior:'smooth'});
}

// PARTICIPANT CARDS
function renderCards(filter = 'ALL') {
  const grid = document.getElementById('participantGrid');
  grid.innerHTML = '';

  participants
    .filter(p => filter === 'ALL' || p.gender === filter)
    .forEach(p => {
      const card = document.createElement('article');
      card.className = 'participant-card';

      const image = document.createElement('img');
      image.className = 'card-image';
      image.src = p.image;
      image.alt = p.name;

      image.onerror = () => {
        const fallback = document.createElement('div');
        fallback.className = 'card-image-fallback';
        fallback.textContent = p.id;
        image.replaceWith(fallback);
      };

      const info = document.createElement('div');
      info.className = 'card-info';

      const number = document.createElement('div');
      number.className = 'card-number';
      number.textContent = p.id;

      const name = document.createElement('div');
      name.className = 'card-name';
      name.textContent = p.name;

      const sub = document.createElement('div');
      sub.className = 'card-sub';
      sub.textContent = 'UNKNOWN ORIGIN / CANDIDATE';

      info.append(number, name, sub);

      const gender = document.createElement('div');
      gender.className = 'card-gender';
      gender.textContent = p.gender;

      card.append(image, info, gender);
      card.onclick = () => openModal(p);

      grid.appendChild(card);
    });
}

function filterCards(filter, btn) {
  document.querySelectorAll('.filter-btn').forEach(b => {
    b.classList.remove('active');
  });

  btn.classList.add('active');
  renderCards(filter);
}

// PROFILE MODAL
function openModal(p) {
  document.getElementById('modalNumber').textContent =
    `SUBJECT ID // ${p.id}`;

  document.getElementById('modalName').textContent = p.name;

  document.getElementById('modalDescription').textContent =
    p.description;

  document.getElementById('modal').style.display = 'flex';
}

function closeModal(event) {
  if (!event || event.target.id === 'modal') {
    document.getElementById('modal').style.display = 'none';
  }
}

renderCards();

</script>
</body>
</html>
