<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Be My Valentine 💖</title>

<style>
* {
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  -webkit-tap-highlight-color: transparent;
}

body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ff3366, #ff99cc, #ffd1dc);
  background-size: 400% 400%;
  animation: bgMove 8s ease infinite;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

@keyframes bgMove {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.card {
  background: white;
  width: 90%;
  max-width: 360px;
  padding: 30px 20px;
  border-radius: 24px;
  text-align: center;
  box-shadow: 0 20px 45px rgba(0,0,0,0.25);
}

h1 {
  color: #ff3366;
  font-size: 24px;
  margin-bottom: 10px;
}

.counter {
  font-size: 14px;
  color: #777;
  margin-bottom: 20px;
}

.buttons {
  position: relative;
  height: 160px;
}

button {
  padding: 16px 34px;
  font-size: 20px;
  border-radius: 40px;
  border: none;
  cursor: pointer;
  touch-action: manipulation;
}

#yesBtn {
  background: linear-gradient(45deg, #ff3366, #ff6699);
  color: white;
  box-shadow: 0 6px 15px rgba(255,51,102,0.5);
}

#noBtn {
  background: #f1f1f1;
  color: #666;
  position: absolute;
  top: 80px;
  left: 50%;
  transform: translateX(-50%);
}

.success {
  display: none;
  font-size: 22px;
  margin-top: 20px;
  color: #ff3366;
  animation: pop 0.6s ease forwards;
}

@keyframes pop {
  from { transform: scale(0.5); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}

/* Floating emojis */
.float {
  position: fixed;
  bottom: -40px;
  font-size: 26px;
  animation: floatUp linear forwards;
  pointer-events: none;
}

@keyframes floatUp {
  to { transform: translateY(-700px); opacity: 0; }
}

/* Insult popup */
.insult {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  background: #ff3366;
  color: white;
  padding: 12px 18px;
  border-radius: 20px;
  font-size: 14px;
  box-shadow: 0 10px 20px rgba(0,0,0,0.3);
  animation: shake 0.4s ease;
}

@keyframes shake {
  0% { transform: translateX(-50%); }
  25% { transform: translateX(-48%); }
  50% { transform: translateX(-52%); }
  75% { transform: translateX(-49%); }
  100% { transform: translateX(-50%); }
}
</style>
</head>

<body>

<div class="card">
  <h1>Will you be my Valentine? 💖</h1>

  <div class="counter">
    NO dodged: <span id="dodgeCount">0</span> times 😏
  </div>

  <div class="buttons">
    <button id="yesBtn">Yes ❤️</button>
    <button id="noBtn">No 💔</button>
  </div>

  <div class="success" id="successMsg">
    FINALLY 😌💘 Ab toh maan hi gaye
  </div>
</div>

<script>
const noBtn = document.getElementById("noBtn");
const yesBtn = document.getElementById("yesBtn");
const successMsg = document.getElementById("successMsg");
const dodgeCountEl = document.getElementById("dodgeCount");

let speedMultiplier = 1;
let dodgeCount = 0;
let insultIndex = 0;

const insults = [
  "Arre bhai 💀",
  "Soch bhi kaise liya NO click karne ka 😭",
  "Skill issue fr 🤡",
  "Bas kar bhai, maan ja 😌",
  "Ego hurt ho raha hai kya? 😏",
  "Itna bhaav kyun kha raha hai 💔",
  "Love se darr lagta hai kya? 😈",
  "Bro fighting destiny 😂",
  "Dil hai ya exam ka question? 🤓",
  "Ab toh YES hi option hai 😌❤️"
];

function moveNoButton() {
  speedMultiplier += 0.3;
  dodgeCount++;
  dodgeCountEl.textContent = dodgeCount;

  // 📳 Vibrate on mobile
  if (navigator.vibrate) {
    navigator.vibrate([40, 30, 40]);
  }

  showInsult();

  const padding = 20;
  const maxX = window.innerWidth - noBtn.offsetWidth - padding;
  const maxY = window.innerHeight - noBtn.offsetHeight - padding;

  const x = Math.random() * maxX;
  const y = Math.random() * maxY;

  noBtn.style.transition = `all ${0.3 / speedMultiplier}s ease`;
  noBtn.style.left = x + "px";
  noBtn.style.top = y + "px";
}

function showInsult() {
  const insult = document.createElement("div");
  insult.className = "insult";
  insult.textContent = insults[insultIndex % insults.length];
  insultIndex++;
  document.body.appendChild(insult);

  setTimeout(() => insult.remove(), 1200);
}

noBtn.addEventListener("touchstart", moveNoButton);
noBtn.addEventListener("mouseover", moveNoButton);

yesBtn.addEventListener("click", () => {
  successMsg.style.display = "block";
  celebrate();
});

function celebrate() {
  const emojis = ["❤️","💖","💘","🎈","🎉","💝"];
  for (let i = 0; i < 45; i++) {
    const item = document.createElement("div");
    item.className = "float";
    item.textContent = emojis[Math.floor(Math.random() * emojis.length)];
    item.style.left = Math.random() * window.innerWidth + "px";
    item.style.animationDuration = (2 + Math.random() * 2) + "s";
    document.body.appendChild(item);

    setTimeout(() => item.remove(), 4000);
  }
}
</script>

</body>
</html>
