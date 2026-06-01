<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A Special Message for You 💐</title>

<!-- Bootstrap (safe CDN) -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

<style>
body {
    background: linear-gradient(135deg, #fdf2f8, #fce7f3, #fbcfe8);
    font-family: 'Segoe UI', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
}

h1 {
    color: #be185d;
}

/* flower cards */
.flower-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    max-width: 900px;
    margin: auto;
    padding: 2rem;
}

.flower-card {
    background: rgba(255,255,255,0.9);
    border-radius: 20px;
    padding: 2rem;
    cursor: pointer;
    transition: 0.3s;
}

.flower-card:hover {
    transform: translateY(-8px) scale(1.05);
}

.flower-icon {
    font-size: 3rem;
}

/* message */
#message-section {
    display: none;
}

.card {
    border-radius: 20px;
}

/* petals */
#petals-container {
    position: fixed;
    inset: 0;
    pointer-events: none;
}

.petal {
    position: absolute;
    width: 15px;
    height: 15px;
    background: pink;
    border-radius: 50%;
    opacity: 0.6;
    animation: fall linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(100vh);
        opacity: 0;
    }
}
</style>
</head>

<body>

<div class="container text-center mt-5">

<h1 class="mb-3">Choose a Flower 🌸</h1>
<p class="mb-5">Each one holds a special thought for you</p>

<div class="flower-container" id="flowerContainer">

<div class="flower-card" data-flower="rose">
    <div class="flower-icon">🌹</div>
    <h4>Rose</h4>
</div>

<div class="flower-card" data-flower="sunflower">
    <div class="flower-icon">🌻</div>
    <h4>Sunflower</h4>
</div>

<div class="flower-card" data-flower="tulip">
    <div class="flower-icon">🌷</div>
    <h4>Tulip</h4>
</div>

<div class="flower-card" data-flower="lavender">
    <div class="flower-icon">💜</div>
    <h4>Lavender</h4>
</div>

</div>

<div id="message-section" class="mt-4">
<div class="card shadow-lg">
<div class="card-body p-4">

<button onclick="goBack()" class="btn btn-outline-secondary mb-3">
← Choose Another
</button>

<h2 id="flower-title"></h2>
<p id="flower-message"></p>
<div id="flower-visual"></div>

</div>
</div>
</div>

</div>

<div id="petals-container"></div>

<script>
const flowerMessages = {
rose: {
title: "🌹 The Rose",
message: "You make things feel special without even trying. I really enjoy talking to you more than I expected.",
visual: "🌹✨"
},
sunflower: {
title: "🌻 The Sunflower",
message: "You bring a kind of warmth that just stays. I like that about you.",
visual: "🌻☀️"
},
tulip: {
title: "🌷 The Tulip",
message: "There's something about you that's simple but meaningful. It stays.",
visual: "🌷💫"
},
lavender: {
title: "💜 The Lavender",
message: "Talking to you feels calm in a way I didn’t expect. I like that space.",
visual: "💜✨"
}
};

const cards = document.querySelectorAll(".flower-card");

cards.forEach(card => {
card.addEventListener("click", () => {
const type = card.dataset.flower;
const data = flowerMessages[type];

document.getElementById("flower-title").textContent = data.title;
document.getElementById("flower-message").textContent = data.message;
document.getElementById("flower-visual").textContent = data.visual;

document.getElementById("flowerContainer").style.display = "none";
document.getElementById("message-section").style.display = "block";

startPetals();
});
});

function goBack() {
document.getElementById("flowerContainer").style.display = "grid";
document.getElementById("message-section").style.display = "none";
stopPetals();
}

/* petals */
let interval;

function startPetals() {
stopPetals(); // prevent stacking

interval = setInterval(() => {
const petal = document.createElement("div");
petal.className = "petal";

petal.style.left = Math.random() * 100 + "vw";
petal.style.animationDuration = (3 + Math.random()*3) + "s";

document.getElementById("petals-container").appendChild(petal);

setTimeout(() => petal.remove(), 6000);
}, 300);
}

function stopPetals() {
clearInterval(interval);
document.getElementById("petals-container").innerHTML = "";
}
</script>

</body>
</html>
