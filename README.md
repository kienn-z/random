<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A Special Message 💐</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display&family=Great+Vibes&family=Inter:wght@300;400&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    font-family: "Inter", sans-serif;
    overflow: hidden;

    /* 🌈 soft gradient glow */
    background: radial-gradient(circle at top, #ffe4ec, #fbcfe8, #e9d5ff);
}

/* ✨ floating glow particles */
.glow {
    position: absolute;
    width: 8px;
    height: 8px;
    background: rgba(255,255,255,0.7);
    border-radius: 50%;
    filter: blur(4px);
    animation: floatGlow 10s linear infinite;
}

@keyframes floatGlow {
    from { transform: translateY(100vh); opacity: 0; }
    50% { opacity: 1; }
    to { transform: translateY(-10vh); opacity: 0; }
}

/* layout */
.container {
    text-align: center;
    padding-top: 60px;
    position: relative;
    z-index: 2;
}

h1 {
    font-family: "Playfair Display", serif;
    color: #be185d;
}

/* flowers */
.flower-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 18px;
    max-width: 450px;
    margin: auto;
}

.flower-card {
    background: rgba(255,255,255,0.85);
    padding: 20px;
    border-radius: 18px;
    cursor: pointer;
    transition: 0.3s;
}
.flower-card:hover {
    transform: scale(1.05);
}

.flower-icon {
    font-size: 2.5rem;
}

/* message */
#message-section {
    display: none;
    margin-top: 20px;
}

/* 💐 bouquet */
.bouquet {
    position: fixed;
    bottom: -100%;
    left: 0;
    width: 100%;
    height: 100%;
    background: url('https://images.pexels.com/photos/931177/pexels-photo-931177.jpeg?auto=compress&cs=tinysrgb&w=1200') center/cover;
    transition: 2s ease;
    z-index: 5;
}

.bouquet.show {
    bottom: 0;
}

/* final text */
.final {
    position: absolute;
    bottom: 80px;
    width: 100%;
    text-align: center;
    color: white;
    font-size: 18px;
    text-shadow: 0 4px 20px rgba(0,0,0,0.5);
    opacity: 0;
    transition: 1s;
}

.bouquet.show .final {
    opacity: 1;
}

/* 🌸 petals */
.petal {
    position: absolute;
    font-size: 14px;
    animation: fall linear forwards;
}
@keyframes fall {
    to { transform: translateY(100vh); }
}
</style>
</head>

<body>

<!-- ✨ glow particles -->
<script>
for (let i = 0; i < 40; i++) {
    const g = document.createElement("div");
    g.className = "glow";
    g.style.left = Math.random()*100 + "vw";
    g.style.animationDuration = (6 + Math.random()*6) + "s";
    document.body.appendChild(g);
}
</script>

<div class="container">

<h1>Choose a Flower 🌸</h1>

<div class="flower-container" id="flowers">
<div class="flower-card" data="rose"><div class="flower-icon">🌹</div>Rose</div>
<div class="flower-card" data="sunflower"><div class="flower-icon">🌻</div>Sunflower</div>
<div class="flower-card" data="tulip"><div class="flower-icon">🌷</div>Tulip</div>
<div class="flower-card" data="lavender"><div class="flower-icon">💜</div>Lavender</div>
</div>

<div id="message-section">
<h2 id="title"></h2>
<p id="msg"></p>
</div>

</div>

<!-- bouquet -->
<div id="bouquet" class="bouquet">
<div class="final">
Happy Birthday 💖<br>
you deserve something soft like this 🌸
</div>
</div>

<script>
const messages = {
rose: "you make things feel special without trying.",
sunflower: "you bring a warmth that stays.",
tulip: "there’s something simple but meaningful about you.",
lavender: "talking to you feels calm in a good way."
};

document.querySelectorAll(".flower-card").forEach(card => {
card.onclick = () => {
const type = card.getAttribute("data");

document.getElementById("title").innerText = type.toUpperCase();
document.getElementById("msg").innerText = messages[type];

document.getElementById("message-section").style.display = "block";

setTimeout(() => {
document.getElementById("bouquet").classList.add("show");
createPetals();
}, 2000);
};
});

/* petals */
function createPetals(){
for(let i=0;i<25;i++){
let p=document.createElement("div");
p.className="petal";
p.innerText="🌸";
p.style.left=Math.random()*100+"vw";
p.style.animationDuration=(3+Math.random()*3)+"s";
document.body.appendChild(p);

setTimeout(()=>p.remove(),6000);
}
}
</script>

</body>
</html>
