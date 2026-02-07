<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>To My Love, Babe 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Playfair+Display&display=swap" rel="stylesheet">

<style>
body{
  margin:0;
  font-family:'Playfair Display',serif;
  background:linear-gradient(120deg,#ffdde1,#ee9ca7);
  text-align:center;
  overflow-x:hidden;
}
h1{color:#b3003b;}

.heart{
  position:fixed;
  top:-10px;
  font-size:22px;
  animation:fall linear infinite;
  z-index:999;
}
@keyframes fall{
  to{transform:translateY(110vh);}
}

.envelope{
  width:320px;height:220px;
  background:#fff;
  margin:30px auto;
  border-radius:15px;
  box-shadow:0 10px 30px rgba(0,0,0,.2);
  cursor:pointer;
  position:relative;
  transition:0.5s;
}
.envelope.open .letter{transform:translateY(-125%);}
.letter{
  background:#fffaf0;
  position:absolute;
  width:100%;height:100%;
  border-radius:15px;
  transition:1s;
  padding:20px;
}
textarea{
  width:100%;height:140px;
  border:none;
  outline:none;
  background:transparent;
  font-family:'Great Vibes',cursive;
  font-size:26px;
  text-align:center;
}

button{
  background:#ff4f79;
  border:none;
  color:white;
  padding:10px 22px;
  border-radius:25px;
  margin:10px;
  font-size:16px;
  cursor:pointer;
}

.gallery{
  border:12px solid pink;
  margin:20px;
  padding:10px;
  border-radius:20px;
}
.gallery img{
  width:90px;height:90px;
  object-fit:cover;
  border-radius:15px;
  margin:5px;
}

#secretNote{
  display:none;
  font-family:'Great Vibes',cursive;
  font-size:28px;
  margin-top:20px;
  color:#b3003b;
}

#countdown{
  font-size:22px;
  margin:20px;
  font-weight:bold;
}

#finalLove{
  display:none;
  font-family:'Great Vibes',cursive;
  font-size:48px;
  color:#ff0055;
  margin-top:20px;
  animation: pulse 1s infinite alternate;
}
@keyframes pulse{
  from{transform:scale(1);}
  to{transform:scale(1.2);}
}
</style>
</head>

<body>

<h1>To My Love, Babe 💖</h1>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/audio/2022/10/26/audio_2a5e9a0c18.mp3">
</audio>
<button onclick="toggleMusic()">🎵 Soft Piano</button>

<div class="envelope" onclick="openEnvelope(this)">
  <div class="letter">
    <textarea readonly>
My dearest Babe,
Every heartbeat, every smile, every little moment
is sweeter because you are in my life.
Happy Valentine’s Day 💖
Always yours, Sumi.
    </textarea>
  </div>
</div>

<h2>🔐 A Special Secret Note</h2>
<input type="password" id="lovePass" placeholder="Enter our special date" style="padding:10px;border-radius:20px;border:none;text-align:center;">
<br>
<button onclick="unlockNote()">Unlock My Heart 💖</button>
<p id="secretNote">
Babe, you are my forever. Every dream I have
starts and ends with you 💕
</p>

<button onclick="generatePoem()">✨ Romantic Poem for Babe</button>
<p id="poem"></p>

<h2>📸 Our Memories</h2>
<input type="file" multiple accept="image/*" onchange="loadImages(event)">
<div class="gallery" id="gallery"></div>

<div id="countdown"></div>

<button onclick="shareLove()">🔗 Copy Your Valentine Link</button>
<p id="shareMsg"></p>

<p id="finalLove">I ❤️ You, Babe!</p>

<script>
// Falling hearts
setInterval(()=>{
  const h=document.createElement("div");
  h.className="heart";
  h.innerHTML="❤️";
  h.style.left=Math.random()*100+"vw";
  h.style.animationDuration=3+Math.random()*5+"s";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),8000);
},300);

// Envelope
function openEnvelope(e){
  e.classList.add("open");
  setTimeout(()=>{document.getElementById("finalLove").style.display="block";},1200);
}

// Music toggle
function toggleMusic(){
  const m=document.getElementById("music");
  m.paused?m.play():m.pause();
}

// Secret Note
function unlockNote(){
  const pass="07021923"; // special date
  const input=document.getElementById("lovePass").value;
  if(input===pass){
    document.getElementById("secretNote").style.display="block";
  }else{
    alert("Hmm… that’s not our secret date 💔");
  }
}

// Poem generator
const poems=[
  "Babe, you are my favorite forever 🌹",
  "Every moment with you feels like a dream 💖",
  "I didn’t fall in love — I chose you 💕",
  "My heart feels at home with you ✨",
  "Every love song finally makes sense because of you 🎶"
];
function generatePoem(){
  document.getElementById("poem").innerText=poems[Math.floor(Math.random()*poems.length)];
}

// Gallery upload
function loadImages(e){
  const g=document.getElementById("gallery");
  for(let f of e.target.files){
    const i=document.createElement("img");
    i.src=URL.createObjectURL(f);
    g.appendChild(i);
  }
}

// Countdown
const v=new Date("Feb 14, 2026 00:00:00").getTime();
setInterval(()=>{
  const n=new Date().getTime();
  const d=v-n;
  document.getElementById("countdown").innerText=
    Math.floor(d/(1000*60*60*24))+" days left until Valentine’s 💕";
},1000);

// Share link
function shareLove(){
  navigator.clipboard.writeText(window.location.href);
  document.getElementById("shareMsg").innerText="Link copied 💌 Send it to your love!";
}
</script>

</body>
</html>
