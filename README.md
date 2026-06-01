# Deskripsi Game

<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>FPS Shooter Mini - Developer</title>

<style>

/* RESET */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

/* BODY */

body{
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:
    radial-gradient(circle at top,#0f172a,#020617 75%);
    overflow:hidden;
    color:white;
    padding:20px;
}

/* BACKGROUND EFFECT */

body::before{
    content:"";
    position:absolute;
    width:500px;
    height:500px;
    background:#00ccff22;
    border-radius:50%;
    filter:blur(120px);
    top:-180px;
    left:-150px;
    z-index:0;
}

body::after{
    content:"";
    position:absolute;
    width:450px;
    height:450px;
    background:#00ffaa22;
    border-radius:50%;
    filter:blur(120px);
    bottom:-180px;
    right:-120px;
    z-index:0;
}

/* ========================= */
/* LOADING SCREEN */
/* ========================= */

#loadingScreen{
    position:fixed;
    inset:0;
    background:#050505;
    display:none;
    justify-content:center;
    align-items:center;
    z-index:9999;
    overflow:hidden;
}

/* Background Glow */

#loadingScreen::before{
    content:'';
    position:absolute;
    width:500px;
    height:500px;
    background:radial-gradient(circle,#00ff99 0%,transparent 70%);
    filter:blur(120px);
    opacity:0.2;
    animation:pulse 3s infinite;
}

/* Loading Container */

.loading-container{
    position:relative;
    width:350px;
    text-align:center;
    color:white;
}

/* Crosshair */

.crosshair{
    position:relative;
    width:90px;
    height:90px;
    margin:0 auto 40px;
    animation:rotate 4s linear infinite;
}

.crosshair span{
    position:absolute;
    background:#00ff99;
    box-shadow:0 0 10px #00ff99;
}

.crosshair span:nth-child(1),
.crosshair span:nth-child(2){
    width:4px;
    height:90px;
    left:50%;
    transform:translateX(-50%);
}

.crosshair span:nth-child(3),
.crosshair span:nth-child(4){
    width:90px;
    height:4px;
    top:50%;
    transform:translateY(-50%);
}

.crosshair span:nth-child(1){ top:-15px; }
.crosshair span:nth-child(2){ bottom:-15px; }
.crosshair span:nth-child(3){ left:-15px; }
.crosshair span:nth-child(4){ right:-15px; }

.center-dot{
    position:absolute;
    width:12px;
    height:12px;
    background:#00ff99;
    border-radius:50%;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    box-shadow:0 0 15px #00ff99;
}

/* Loading Text */

.loading-text{
    font-size:22px;
    letter-spacing:4px;
    margin-bottom:20px;
    color:#00ff99;
    text-shadow:0 0 10px #00ff99;
}

/* Progress Bar */

.progress-bar{
    width:100%;
    height:10px;
    background:#111;
    border:1px solid #00ff99;
    overflow:hidden;
    border-radius:20px;
    box-shadow:0 0 10px rgba(0,255,153,0.3);
}

.progress{
    height:100%;
    width:0%;
    background:linear-gradient(90deg,#00ff99,#00ccff);
    animation:loading 4s forwards;
    box-shadow:0 0 15px #00ff99;
}

/* Percentage */

.percent{
    margin-top:15px;
    color:#aaa;
    font-size:14px;
    animation:blink 1s infinite;
}

/* ========================= */
/* MAIN CONTAINER */
/* ========================= */

.container{
    position:relative;
    z-index:2;

    width:1000px;
    max-width:95%;

    background:rgba(255,255,255,0.05);

    border:1px solid rgba(255,255,255,0.08);

    backdrop-filter:blur(12px);

    border-radius:28px;

    padding:28px;

    box-shadow:
    0 0 30px rgba(0,204,255,0.15);
}

/* TITLE */

.title{
    text-align:center;
    margin-bottom:24px;
}

.title h1{
    font-size:56px;
    color:#00ccff;
    text-shadow:0 0 15px #00ccff;
    margin-bottom:8px;
    letter-spacing:2px;
}

.title p{
    color:#d1d5db;
    font-size:16px;
}

/* GRID */

.grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:18px;
}

/* CARD */

.card{
    background:rgba(255,255,255,0.04);

    border:1px solid rgba(255,255,255,0.08);

    border-radius:22px;

    padding:22px;

    transition:0.25s;
}

.card:hover{
    transform:translateY(-4px);

    box-shadow:
    0 0 20px rgba(0,204,255,0.15);
}

.card h2{
    font-size:30px;
    color:#00ffaa;
    margin-bottom:18px;
}

.card p{
    font-size:16px;
    line-height:1.8;
    color:#e5e7eb;
    margin-bottom:12px;
}

/* BUTTON */

.startBtn{
    margin:28px auto 0;

    display:flex;
    justify-content:center;
    align-items:center;

    width:420px;
    max-width:100%;

    padding:18px;

    border-radius:18px;

    text-decoration:none;

    font-size:24px;
    font-weight:bold;

    color:white;

    background:
    linear-gradient(45deg,#00ccff,#00ffaa);

    transition:0.25s;

    cursor:pointer;
}

.startBtn:hover{
    transform:scale(1.02);

    box-shadow:
    0 0 25px rgba(0,255,170,0.45);
}

/* ANIMATION */

@keyframes loading{
    0%{ width:0%; }
    100%{ width:100%; }
}

@keyframes rotate{
    100%{
        transform:rotate(360deg);
    }
}

@keyframes pulse{
    0%,100%{
        transform:scale(1);
        opacity:0.2;
    }
    50%{
        transform:scale(1.1);
        opacity:0.35;
    }
}

@keyframes blink{
    0%,100%{ opacity:1; }
    50%{ opacity:0.4; }
}

/* MOBILE */

@media(max-width:850px){

    body{
        overflow:auto;
        padding:25px 0;
    }

    .grid{
        grid-template-columns:1fr;
    }

    .title h1{
        font-size:40px;
    }

    .startBtn{
        width:100%;
    }

}

</style>
</head>

<body>

<!-- LOADING SCREEN -->

<div id="loadingScreen">

    <div class="loading-container">

        <div class="crosshair">
            <span></span>
            <span></span>
            <span></span>
            <span></span>

            <div class="center-dot"></div>
        </div>

        <div class="loading-text">
            LOADING...
        </div>

        <div class="progress-bar">
            <div class="progress"></div>
        </div>

        <div class="percent">
            Initializing FPS Engine...
        </div>

    </div>

</div>

<!-- MAIN MENU -->

<div class="container">

    <!-- TITLE -->

    <div class="title">

        <h1>SKI GVX SHOOTER </h1>

        <p>
        Game FPS sederhana berbasis web dengan gameplay cepat dan modern.
        </p>

    </div>

    <!-- GRID -->

    <div class="grid">

        <!-- DEVELOPER -->

        <div class="card">

            <h2>👨‍💻 Developer</h2>

            <p><b>Nama :</b> Skistar Games</p>

            <p><b>Project :</b> FPS Shooter Mini</p>

            <p><b>Genre :</b> First Person Shooter</p>

            <p><b>Dibuat Dengan :</b> HTML, CSS, JavaScript</p>

            <p>
            Project ini dibuat untuk melatih kemampuan
            membuat game menggunakan HTML Canvas
            dan JavaScript.
            </p>

        </div>

        <!-- ABOUT GAME -->

        <div class="card">

            <h2>🎮 Tentang Game</h2>

            <p>
            FPS Shooter Mini adalah game FPS ringan
            berbasis browser dengan berbagai jenis
            senjata dan efek unik.
            </p>

            <p>
            Tujuan bermain game ini adalah pemain harus mengalahkan musuh sebanyak
            mungkin untuk mempertahankan dan  mendapatkan score tertinggi.
            </p>

            <p>
            Di Game buatan saya ini memiliki tampilan modern,
            gameplay cepat, cocok untuk mengisi waktu luang anda, dan kontrol sederhana.
            </p>

        </div>

    </div>

    <!-- BUTTON -->

    <a href="#" class="startBtn" id="playBtn">

        ▶ MASUK MENU GAME

    </a>

</div>

<script>

const playBtn = document.getElementById("playBtn");
const loadingScreen = document.getElementById("loadingScreen");

playBtn.addEventListener("click", function(e){

    e.preventDefault();

    /* SHOW LOADING */

    loadingScreen.style.display = "flex";

    /* PINDAH HALAMAN */

    setTimeout(() => {

        window.location.href =
        "./FPS Shooter Mini By Sakhi.Com.Html";

    },4000);

});

</script>

</body>
</html>

# FPS Shooter Mini


<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FPS Shooter Mini By Sakhi</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    overflow:hidden;
    background:black;   
    cursor:crosshair;
}

canvas{
    display:block;
    background:radial-gradient(circle at center,#222 0%,#000 100%);
}

#menu{
    position:absolute;
    width:100%;
    height:100%;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    background:radial-gradient(circle,#222,#000);
    color:white;
    z-index:100;
}

#menu h1{
    font-size:55px;
    color:#00ccff;
    margin-bottom:20px;
    text-shadow:0 0 20px #00ccff;
    text-align:center;
}

#menu input,
#menu select{
    padding:15px;
    width:280px;
    border:none;
    border-radius:10px;
    margin-bottom:20px;
    font-size:18px;
    text-align:center;
}

#menu button{
    padding:15px 30px;
    border:none;
    border-radius:10px;
    background:#00ccff;
    color:white;
    font-size:20px;
    cursor:pointer;
}

#menu button:hover{
    background:#00ffaa;
}

.infoBox{
    margin-top:20px;
    width:360px;
    background:rgba(255,255,255,0.08);
    border:1px solid #00ccff;
    border-radius:15px;
    padding:15px;
    color:white;
}

.infoTitle{
    text-align:center;
    color:#00ccff;
    margin-bottom:10px;
    font-size:22px;
}

.infoItem{
    margin:8px 0;
    font-size:16px;
    display:flex;
    justify-content:space-between;
    border-bottom:1px solid rgba(255,255,255,0.1);
    padding-bottom:5px;
}

.key{
    color:#00ffaa;
    font-weight:bold;
}

.ui{
    position:absolute;
    top:15px;
    left:15px;
    color:white;
    z-index:10;
    font-size:20px;
}

#leaderboard{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    width:380px;
    max-height:500px;
    overflow-y:auto;
    background:rgba(0,0,0,0.95);
    color:white;
    padding:20px;
    border-radius:20px;
    border:2px solid #00ccff;
    z-index:200;
    display:none;
}

#leaderboard h2{
    text-align:center;
    margin-bottom:15px;
    color:#00ccff;
}

#leaderboard table{
    width:100%;
    border-collapse:collapse;
}

#leaderboard th,
#leaderboard td{
    padding:10px;
    border-bottom:1px solid #444;
    text-align:center;
}

#leaderboard button{
    width:100%;
    margin-top:15px;
    padding:12px;
    border:none;
    border-radius:10px;
    background:#00ccff;
    color:white;
    font-size:18px;
    cursor:pointer;
}

#leaderboard button:hover{
    background:#00ffaa;
}
</style>
</head>

<body>

<div id="menu">

<h1>FPS SHOOTER MINI BY SKISTAR GAMES</h1>

<input type="text" id="nameInput" placeholder="Masukkan Nama">

<select id="difficulty">
<option value="difficulty" selected>Difficulty</option>
<option value="training">Training Mode</option>
<option value="easy">Easy</option>
<option value="normal">Normal</option>
<option value="hard">Hard</option>
<option value="veryhard">Very Hard</option>
</select>

<button onclick="startGame()">▶ PLAY</button>

<div class="infoBox">
    
<div class="infoTitle">
Cara Bermain
</div>

<div class="infoItem">
<span>Gerak</span>
<span class="key">W A S D</span>
</div>

<div class="infoItem">
<span>Tembak</span>
<span class="key">Klik Kiri</span>
</div>

<div class="infoItem">
<span>Bidik</span>
<span class="key">Klik Kanan</span>
</div>

<div class="infoItem">
<span>1</span>
<span class="key">Bazooka</span>
</div>

<div class="infoItem">
<span>2</span>
<span class="key">Shotgun</span>
</div>

<div class="infoItem">
<span>3</span>
<span class="key">Sniper</span>
</div>

<div class="infoItem">
<span>4</span>
<span class="key">Submachine Gun</span>
</div>

<div class="infoItem">
<span>5</span>
<span class="key">Granat</span>
</div>

<div class="infoItem">
<span>6</span>
<span class="key">Laser Gun</span>
</div>

<div class="infoItem">
<span>7</span>
<span class="key">Assault Rifle</span>
</div>

<div class="infoItem">
<span>8</span>
<span class="key">Pistol</span>
</div>

<div class="infoItem">
<span>9</span>
<span class="key">Samurai</span>
</div>

</div>
</div>

<div class="ui">

👤 Player:
<span id="playerNameText">-</span>
<br>

🎮 Mode:
<span id="modeText">-</span>
<br>

❤️ Nyawa:
<span id="healthText">3</span>
<br>

🔫 Senjata:
<span id="weaponText">Bazoka</span>
<br>

🎯 Score:
<span id="score">0</span>

</div>

<div id="leaderboard">

<h2>🏆 Klasemen Top Player</h2>

<table>
<thead>
<tr>
<th>Peringkat</th>
<th>Name Player</th>
<th>Score</th>
</tr>
</thead>

<tbody id="leaderboardBody"></tbody>
</table>

<button onclick="resetLeaderboard()">
🗑 RESET TOP PLAYER
</button>

<button onclick="location.reload()">
▶ MAIN LAGI
</button>

</div>

<canvas id="game"></canvas>

<script>

const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

canvas.width = innerWidth;
canvas.height = innerHeight;

let gameStarted = false;
let playerName = "Player";

let difficulty = "normal";
let enemySpawnSpeed = 1000;

let score = 0;
let health = 3;

const bullets = [];
const enemies = [];
const particles = [];
const lasers = [];
const fires = [];
const slashes = [];
const keys = {};

const player = {
    x: canvas.width/2,
    y: canvas.height/2,
    radius:20,
    speed:7,
    aim:false
};

const mouse = {
    x:canvas.width/2,
    y:canvas.height/2
};

let weapon = "bazoka";

const weapons = {

    bazoka:{
        speed:10,
        size:12,
        bullets:1,
        spread:0
    },

    shotgun:{
        speed:10,
        size:4,
        bullets:5,
        spread:0.4
    },

    sniper:{
        speed:80,
        size:7,
        bullets:1,
        spread:0
    },

    smg:{
        speed:20,
        size:3,
        bullets:1,
        spread:0.08
    },

    granat:{
        speed:5,
        size:15,
        bullets:1,
        spread:0
    },

    laser:{
        speed:100,
        size:5,
        bullets:1,
        spread:0
    },

    rifle:{
        speed:35,
        size:5,
        bullets:1,
        spread:0.04
    },

    pistol:{
        speed:28,
        size:5,
        bullets:1,
        spread:0.01
    },

    samurai:{
        range:180
    }
};

const audioCtx =
new (window.AudioContext ||
window.webkitAudioContext)();

function playShootSound(type){

    const osc =
    audioCtx.createOscillator();

    const gain =
    audioCtx.createGain();

    osc.connect(gain);
    gain.connect(audioCtx.destination);

    if(type === "bazoka"){
        osc.type = "sawtooth";
        osc.frequency.value = 90;
    }

    if(type === "shotgun"){
        osc.type = "square";
        osc.frequency.value = 170;
    }

    if(type === "sniper"){
        osc.type = "triangle";
        osc.frequency.value = 450;
    }

    if(type === "smg"){
        osc.type = "square";
        osc.frequency.value = 280;
    }

    if(type === "granat"){
        osc.type = "sawtooth";
        osc.frequency.value = 120;
    }

    if(type === "laser"){
        osc.type = "sine";
        osc.frequency.value = 900;
    }

    if(type === "rifle"){
        osc.type = "square";
        osc.frequency.value = 320;
    }

    if(type === "pistol"){
        osc.type = "triangle";
        osc.frequency.value = 230;
    }

    if(type === "samurai"){
        osc.type = "sawtooth";
        osc.frequency.value = 600;
    }

    gain.gain.setValueAtTime(
    0.15,
    audioCtx.currentTime
    );

    gain.gain.exponentialRampToValueAtTime(
    0.001,
    audioCtx.currentTime + 0.12
    );

    osc.start();
    osc.stop(audioCtx.currentTime + 0.12);
}

function playHitSound(){

    const osc =
    audioCtx.createOscillator();

    const gain =
    audioCtx.createGain();

    osc.connect(gain);
    gain.connect(audioCtx.destination);

    osc.type = "triangle";

    osc.frequency.setValueAtTime(
    300,
    audioCtx.currentTime
    );

    osc.frequency.exponentialRampToValueAtTime(
    80,
    audioCtx.currentTime + 0.08
    );

    gain.gain.setValueAtTime(
    0.18,
    audioCtx.currentTime
    );

    gain.gain.exponentialRampToValueAtTime(
    0.001,
    audioCtx.currentTime + 0.08
    );

    osc.start();
    osc.stop(audioCtx.currentTime + 0.08);
}

function startGame(){

    const input =
    document.getElementById("nameInput");

    playerName = input.value.trim();

    difficulty =
    document.getElementById("difficulty").value;

    if(playerName === ""){
        alert("⚠ Masukkan Nama Anda Terlebih Dahulu!");
        return;
    }

    if(difficulty === "difficulty"){
        alert("⚠ Pilih Difficulty Terlebih Dahulu!");
        return;
    }

    document.getElementById(
    "modeText").innerText =
    difficulty.toUpperCase();

    if(difficulty === "training"){
        enemySpawnSpeed = 3000;
        health = 999;
    }

    if(difficulty === "easy"){
        enemySpawnSpeed = 2000;
        health = 5;
    }

    if(difficulty === "normal"){
        enemySpawnSpeed = 1000;
        health = 4;
    }

    if(difficulty === "hard"){
        enemySpawnSpeed = 650;
        health = 3;
    }

    if(difficulty === "veryhard"){
        enemySpawnSpeed = 450;
        health = 2;
    }

    document.getElementById(
    "healthText").innerText = health;

    clearInterval(enemyLoop);

    enemyLoop =
    setInterval(spawnEnemy,enemySpawnSpeed);

    document.getElementById(
    "playerNameText").innerText =
    playerName;

    document.getElementById(
    "menu").style.display = "none";

    gameStarted = true;
}

let leaderboard =
JSON.parse(localStorage.getItem(
"fpsLeaderboard")) || [];

function updateLeaderboard(){

    leaderboard.sort(
    (a,b)=>b.score-a.score);

    const body =
    document.getElementById(
    "leaderboardBody");

    body.innerHTML = "";

    leaderboard.forEach((player,index)=>{

        body.innerHTML += `
        <tr>
            <td>#${index+1}</td>
            <td>${player.name}</td>
            <td>${player.score}</td>
        </tr>
        `;
    });
}

function saveScore(){

    if(difficulty === "training"){
        return;
    }

    const existingPlayer =
    leaderboard.find(
        p => p.name.toLowerCase() ===
        playerName.toLowerCase()
    );

    if(existingPlayer){

        if(score > existingPlayer.score){
            existingPlayer.score = score;
        }

    }else{

        leaderboard.push({
            name: playerName,
            score: score
        });
    }

    leaderboard.sort(
    (a,b)=>b.score-a.score);

    localStorage.setItem(
    "fpsLeaderboard",
    JSON.stringify(leaderboard)
    );
}

function resetLeaderboard(){

    const confirmReset = confirm(
    "Yakin ingin reset semua top player?"
    );

    if(confirmReset){

        localStorage.removeItem(
        "fpsLeaderboard"
        );

        leaderboard = [];

        updateLeaderboard();

        alert(
        "✅ Top Player berhasil direset!"
        );
    }
}

document.addEventListener(
"mousemove",(e)=>{

    mouse.x = e.clientX;
    mouse.y = e.clientY;
});

document.addEventListener(
"keydown",(e)=>{

    keys[e.key.toLowerCase()] = true;

    if(e.key === "1") weapon = "bazoka";
    if(e.key === "2") weapon = "shotgun";
    if(e.key === "3") weapon = "sniper";
    if(e.key === "4") weapon = "smg";
    if(e.key === "5") weapon = "granat";
    if(e.key === "6") weapon = "laser";
    if(e.key === "7") weapon = "rifle";
    if(e.key === "8") weapon = "pistol";
    if(e.key === "9") weapon = "samurai";

    document.getElementById(
    "weaponText").innerText =
    weapon.charAt(0).toUpperCase() +
    weapon.slice(1);
});

document.addEventListener(
"keyup",(e)=>{
    keys[e.key.toLowerCase()] = false;
});

document.addEventListener(
"mousedown",(e)=>{

    if(!gameStarted) return;

    if(e.button === 0){
        shoot();
    }

    if(e.button === 2){
        player.aim = true;
    }
});

document.addEventListener(
"mouseup",(e)=>{

    if(e.button === 2){
        player.aim = false;
    }
});

document.addEventListener(
"contextmenu",(e)=>{
    e.preventDefault();
});

function shoot(){

    playShootSound(weapon);

 if(weapon === "samurai"){

    const angle =
    Math.atan2(
        mouse.y - player.y,
        mouse.x - player.x
    );

    // random arah tebas
    const side =
    Math.random() > 0.5 ? 1 : -1;

    slashes.push({
        x:player.x,
        y:player.y,
        angle,
        side,
        life:14
    });

    enemies.forEach((enemy,eIndex)=>{

        const dist =
        Math.hypot(
            enemy.x-player.x,
            enemy.y-player.y
        );

        if(dist < 190){

            playHitSound();

            // darah tebal
            for(let i=0;i<50;i++){

                particles.push({

                    x:enemy.x,
                    y:enemy.y,

                    radius:
                    Math.random()*7+2,

                    dx:
                    (Math.random()-0.5)*20,

                    dy:
                    (Math.random()-0.5)*20,

                    life:60,

                    color:
                    Math.random()>0.3
                    ? "#ff0000"
                    : "#990000"
                });
            }

            createExplosion(
                enemy.x,
                enemy.y,
                "#ff0000"
            );

            enemies.splice(eIndex,1);

            score += 30;

            document.getElementById(
            "score").innerText = score;
        }
    });

    return;
}
    const gun = weapons[weapon];

    const baseAngle =
    Math.atan2(
        mouse.y - player.y,
        mouse.x - player.x
    );

    for(let i=0;i<gun.bullets;i++){

        const angle =
        baseAngle +
        (Math.random()-0.5)
        * gun.spread;

        bullets.push({

            x: player.x,
            y: player.y,

            radius: gun.size,
            speed: gun.speed,

            dx: Math.cos(angle),
            dy: Math.sin(angle),

            weaponType: weapon,

            trail:[]
        });

        if(weapon === "laser"){

            const laserLength =
            Math.max(
                canvas.width,
                canvas.height
            ) * 2;

            const endX =
            player.x +
            Math.cos(angle) *
            laserLength;

            const endY =
            player.y +
            Math.sin(angle) *
            laserLength;

            lasers.push({

                x1: player.x,
                y1: player.y,

                x2: endX,
                y2: endY,

                life:10
            });

            enemies.forEach((enemy,eIndex)=>{

                const A =
                enemy.x - player.x;

                const B =
                enemy.y - player.y;

                const C =
                endX - player.x;

                const D =
                endY - player.y;

                const dot =
                A * C + B * D;

                const lenSq =
                C * C + D * D;

                let param =
                dot / lenSq;

                if(param < 0) param = 0;
                if(param > 1) param = 1;

                const xx =
                player.x + param * C;

                const yy =
                player.y + param * D;

                const dist =
                Math.hypot(
                    enemy.x - xx,
                    enemy.y - yy
                );

                if(dist < enemy.radius + 12){

                    playHitSound();

                    createExplosion(
                        enemy.x,
                        enemy.y,
                        enemy.color
                    );

                    enemies.splice(eIndex,1);

                    score += 15;

                    document.getElementById(
                    "score").innerText =
                    score;
                }
            });

            bullets.pop();
        }
    }
}

function spawnEnemy(){
    if(enemies.length > 50) return;

    if(!gameStarted) return;

    let x;
    let y;

    if(Math.random() < 0.5){

        x = Math.random() * canvas.width;

        y = Math.random() < 0.5
        ? -50
        : canvas.height + 50;

    }else{

        x = Math.random() < 0.5
        ? -50
        : canvas.width + 50;

        y = Math.random() * canvas.height;
    }

    let enemyCount =
    difficulty === "veryhard" ? 2 : 1;

    for(let i=0;i<enemyCount;i++){

        enemies.push({

            x,
            y,

            radius:
            difficulty === "veryhard"
            ? 35 + Math.random()*15
            : 20 + Math.random()*15,

            speed:
            difficulty === "training"
            ? 0.4
            : difficulty === "veryhard"
            ? 3
            : difficulty === "hard"
            ? 2
            : difficulty === "easy"
            ? 0.7
            : 1.2,

            color:
            `hsl(${Math.random()*360},
            100%,50%)`
        });
    }
}

let enemyLoop =
setInterval(spawnEnemy,1000);

function createExplosion(x,y,color){

    for(let i=0;i<35;i++){

        particles.push({

            x,
            y,

            radius:
            Math.random()*6,

            dx:
            (Math.random()-0.5)*14,

            dy:
            (Math.random()-0.5)*14,

            life:50,
            color
        });
    }
}

function createFireEffect(x,y){

    for(let i=0;i<20;i++){

        fires.push({
            x,
            y,
            radius:Math.random()*10+5,
            dx:(Math.random()-0.5)*3,
            dy:-Math.random()*4,
            life:40 + Math.random()*20,
            color:[
                "#ff2200",
                "#ff6600",
                "#ffaa00",
                "#ffff66"
            ][Math.floor(Math.random()*4)]
        });
    }
}

function grenadeExplosion(x,y){

    playHitSound();

    for(let i=0;i<35;i++){

        particles.push({
            x,
            y,
            radius:Math.random()*8,
            dx:(Math.random()-0.5)*20,
            dy:(Math.random()-0.5)*20,
            life:70,
            color:`hsl(${Math.random()*60},100%,50%)`
        });
    }

    enemies.forEach((enemy,eIndex)=>{

        const dist =
        Math.hypot(
            x - enemy.x,
            y - enemy.y
        );

        if(dist < 140){

            createExplosion(
                enemy.x,
                enemy.y,
                enemy.color
            );

            enemies.splice(eIndex,1);

            score += 20;

            document.getElementById(
            "score").innerText = score;
        }
    });
}

function gameOver(){

    gameStarted = false;

    saveScore();

    updateLeaderboard();

    document.getElementById(
    "leaderboard").style.display =
    "block";
}

function update(){

    if(!gameStarted) return;

    if(keys["w"]) player.y -= player.speed;
    if(keys["s"]) player.y += player.speed;
    if(keys["a"]) player.x -= player.speed;
    if(keys["d"]) player.x += player.speed;

    if(player.x < player.radius){
        player.x = player.radius;
    }

    if(player.x > canvas.width - player.radius){
        player.x = canvas.width - player.radius;
    }

    if(player.y < player.radius){
        player.y = player.radius;
    }

    if(player.y > canvas.height - player.radius){
        player.y = canvas.height - player.radius;
    }

    bullets.forEach((b,bIndex)=>{

        b.trail.push({
            x:b.x,
            y:b.y
        });

        if(b.trail.length > 4){
            b.trail.shift();
        }

        b.x += b.dx * b.speed;
        b.y += b.dy * b.speed;

        if(
            b.x < 0 ||
            b.x > canvas.width ||
            b.y < 0 ||
            b.y > canvas.height
        ){
            bullets.splice(bIndex,1);
        }
    });

    enemies.forEach((enemy,eIndex)=>{

        const angle =
        Math.atan2(
            player.y - enemy.y,
            player.x - enemy.x
        );

        enemy.x +=
        Math.cos(angle) * enemy.speed;

        enemy.y +=
        Math.sin(angle) * enemy.speed;

        const distPlayer =
        Math.hypot(
            player.x - enemy.x,
            player.y - enemy.y
        );

        if(
            distPlayer <
            player.radius + enemy.radius
        ){

            enemies.splice(eIndex,1);

            if(difficulty !== "training"){
                health--;

                document.getElementById(
                "healthText").innerText =
                health;

                if(health <= 0){
                    gameOver();
                }
            }
        }

        bullets.forEach((bullet,bIndex)=>{

            const dist =
            Math.hypot(
                bullet.x - enemy.x,
                bullet.y - enemy.y
            );

            if(
                dist <
                enemy.radius +
                bullet.radius
            ){

                playHitSound();

                if(
                    bullet.weaponType ===
                    "granat"
                ){

                    grenadeExplosion(
                        bullet.x,
                        bullet.y
                    );

                }else{

                    createExplosion(
                        enemy.x,
                        enemy.y,
                        enemy.color
                    );

                    if(
                        bullet.weaponType ===
                        "bazoka"
                    ){
                        createFireEffect(
                            enemy.x,
                            enemy.y
                        );
                    }

                    enemies.splice(eIndex,1);

                    score +=
                    bullet.weaponType === "smg"
                    ? 5
                    : bullet.weaponType === "laser"
                    ? 15
                    : bullet.weaponType === "bazoka"
                    ? 25
                    : bullet.weaponType === "rifle"
                    ? 12
                    : bullet.weaponType === "pistol"
                    ? 8
                    : 10;

                    document.getElementById(
                    "score").innerText = score;
                }

                bullets.splice(bIndex,1);
            }
        });
    });

    particles.forEach((p,pIndex)=>{

        p.x += p.dx;
        p.y += p.dy;

        p.life--;

        if(p.life <= 0){
            particles.splice(pIndex,1);
        }
    });

    fires.forEach((f,index)=>{

        f.x += f.dx;
        f.y += f.dy;

        f.radius *= 0.96;

        f.life--;

        if(f.life <= 0){
            fires.splice(index,1);
        }
    });

    lasers.forEach((laser,index)=>{
        laser.life--;

        if(laser.life <= 0){
            lasers.splice(index,1);
        }
    });

    slashes.forEach((s,index)=>{
        s.life--;

        if(s.life <= 0){
            slashes.splice(index,1);
        }
    });
}

function draw(){

    ctx.clearRect(
    0,0,
    canvas.width,
    canvas.height
    );

    const angle =
    Math.atan2(
        mouse.y - player.y,
        mouse.x - player.x
    );

    ctx.save();

    ctx.translate(
    player.x,
    player.y
    );

    ctx.rotate(angle);

    ctx.fillStyle =
    player.aim
    ? "#00ff99"
    : "#00ccff";

    ctx.beginPath();

    ctx.arc(
        0,0,
        player.radius,
        0,
        Math.PI*2
    );

    ctx.fill();

    ctx.fillStyle = "white";

    if(weapon === "samurai"){

    // posisi pedang agak diagonal
    ctx.rotate(0.12);

    // gagang utama
    ctx.fillStyle = "#1a1a1a";

    ctx.fillRect(
        -18,-5,
        42,10
    );

    // motif lilitan handle
    ctx.strokeStyle = "#00ffaa";

    ctx.lineWidth = 2;

    for(let i=-14;i<20;i+=6){

        ctx.beginPath();

        ctx.moveTo(i,-5);

        ctx.lineTo(i+8,5);

        ctx.stroke();
    }

    // pelindung tangan
    ctx.fillStyle = "#c9a227";

    ctx.fillRect(
        20,-10,
        7,20
    );

    // efek gradasi besi
    const blade =
    ctx.createLinearGradient(
        20,0,150,0
    );

    blade.addColorStop(0,"#666");
    blade.addColorStop(0.2,"#ffffff");
    blade.addColorStop(0.5,"#dddddd");
    blade.addColorStop(0.8,"#ffffff");
    blade.addColorStop(1,"#666");

    ctx.fillStyle = blade;

    // bentuk katana melengkung
    ctx.beginPath();

    ctx.moveTo(22,-3);

    ctx.quadraticCurveTo(
        90,-10,
        140,-2
    );

    ctx.lineTo(158,0);

    ctx.quadraticCurveTo(
        90,10,
        22,3
    );

    ctx.closePath();

    ctx.fill();

    // garis tajam cahaya
    ctx.strokeStyle =
    "rgba(255,255,255,0.9)";

    ctx.lineWidth = 1;

    ctx.beginPath();

    ctx.moveTo(35,-1);

    ctx.quadraticCurveTo(
        100,-6,
        145,-1
    );

    ctx.stroke();

    // glow tipis
    ctx.shadowBlur = 15;

    ctx.shadowColor =
    "rgba(255,255,255,0.7)";

}else{

        ctx.fillStyle = "white";

        ctx.fillRect(
            0,-5,
            55,10
        );
    }

    ctx.restore();

  slashes.forEach(s=>{

    ctx.save();

    ctx.translate(s.x,s.y);

    ctx.rotate(s.angle);

    ctx.strokeStyle = "#ffffff";

    ctx.lineWidth = 14;

    ctx.shadowBlur = 10;

    ctx.shadowColor = "#ffffff";

    ctx.beginPath();

    if(s.side === 1){

        // tebas kanan
        ctx.arc(
            0,
            0,
            140,
            -0.9,
            0.3
        );

    }else{

        // tebas kiri
        ctx.arc(
            0,
            0,
            140,
            -0.3,
            0.9
        );
    }

    ctx.stroke();

    // efek angin slash
    ctx.strokeStyle =
    "rgba(255,255,255,0.3)";

    ctx.lineWidth = 28;

    ctx.stroke();

    ctx.restore();
});
    lasers.forEach(laser=>{

        ctx.strokeStyle = "#ff00ff";
        ctx.lineWidth = 6;
        ctx.shadowBlur = 10;
        ctx.shadowColor = "#ff00ff";

        ctx.beginPath();
        ctx.moveTo(laser.x1,laser.y1);
        ctx.lineTo(laser.x2,laser.y2);
        ctx.stroke();

        ctx.shadowBlur = 0;
    });

    ctx.strokeStyle = "red";

    ctx.beginPath();

    ctx.moveTo(mouse.x - 10,mouse.y);
    ctx.lineTo(mouse.x + 10,mouse.y);

    ctx.moveTo(mouse.x,mouse.y - 10);
    ctx.lineTo(mouse.x,mouse.y + 10);

    ctx.stroke();

    bullets.forEach(b=>{

        b.trail.forEach((t,index)=>{

            ctx.globalAlpha =
            index / b.trail.length;

            ctx.fillStyle =
            b.weaponType === "smg"
            ? "#00ff00"
            : b.weaponType === "rifle"
            ? "#ffaa00"
            : b.weaponType === "pistol"
            ? "#00ccff"
            : "#ffffff";

            ctx.beginPath();

            ctx.arc(
                t.x,
                t.y,
                b.radius/2,
                0,
                Math.PI*2
            );

            ctx.fill();
        });

        ctx.globalAlpha = 1;

        ctx.shadowBlur = 0;

        if(b.weaponType === "bazoka"){
            ctx.fillStyle = "orange";
            ctx.shadowBlur = 20;
            ctx.shadowColor = "orange";
        }

        if(b.weaponType === "shotgun"){
            ctx.fillStyle = "yellow";
        }

        if(b.weaponType === "sniper"){
            ctx.fillStyle = "white";
        }

        if(b.weaponType === "smg"){
            ctx.fillStyle = "#00ff00";
            ctx.shadowBlur = 10;
            ctx.shadowColor = "#00ff00";
        }

        if(b.weaponType === "granat"){
            ctx.fillStyle = "#00ccff";
            ctx.shadowBlur = 20;
            ctx.shadowColor = "#00ccff";
        }

        if(b.weaponType === "laser"){
            ctx.fillStyle = "#ff00ff";
            ctx.shadowBlur = 25;
            ctx.shadowColor = "#ff00ff";
        }

        if(b.weaponType === "rifle"){
            ctx.fillStyle = "#ffaa00";
            ctx.shadowBlur = 15;
            ctx.shadowColor = "#ffaa00";
        }

        if(b.weaponType === "pistol"){
            ctx.fillStyle = "#00ccff";
            ctx.shadowBlur = 10;
            ctx.shadowColor = "#00ccff";
        }

        ctx.beginPath();

        ctx.arc(
            b.x,
            b.y,
            b.radius,
            0,
            Math.PI*2
        );

        ctx.fill();
    });

    fires.forEach(f=>{

        ctx.globalAlpha = f.life / 60;

        ctx.fillStyle = f.color;

        ctx.shadowBlur = 25;
        ctx.shadowColor = f.color;

        ctx.beginPath();

        ctx.arc(
            f.x,
            f.y,
            f.radius,
            0,
            Math.PI*2
        );

        ctx.fill();
    });

    ctx.globalAlpha = 1;
    ctx.shadowBlur = 0;

    enemies.forEach(enemy=>{

        ctx.fillStyle = enemy.color;

        ctx.beginPath();

        ctx.arc(
            enemy.x,
            enemy.y,
            enemy.radius,
            0,
            Math.PI*2
        );

        ctx.fill();
    });

    particles.forEach(p=>{

        ctx.globalAlpha = p.life / 70;

        ctx.fillStyle = p.color;

        ctx.beginPath();

        ctx.arc(
            p.x,
            p.y,
            p.radius,
            0,
            Math.PI*2
        );

        ctx.fill();
    });

    ctx.globalAlpha = 1;
}

function animate(){

    update();
    draw();

    requestAnimationFrame(animate);
}

animate();

window.addEventListener(
"resize",()=>{

    canvas.width = innerWidth;
    canvas.height = innerHeight;
});

</script>

</body>
</html>
