<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Be My Valentine 💘</title>

<style>
  body {
    margin: 0;
    height: 100vh;
    overflow: hidden;
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    font-family: 'Comic Sans MS', cursive, sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .card {
    background: white;
    padding: 30px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,0.25);
    max-width: 90%;
    width: 350px;
    position: relative;
    z-index: 10;
  }

  h1 {
    color: #ff4d6d;
    margin-bottom: 25px;
    font-size: 26px;
  }

  button {
    padding: 14px 26px;
    font-size: 18px;
    border: none;
    border-radius: 30px;
    cursor: pointer;
    transition: all 0.3s ease;
    touch-action: manipulation;
  }

  #yesBtn {
    background: #ff4d6d;
    color: white;
    margin-right: 10px;
  }

  #noBtn {
    background: #ddd;
    color: #333;
    position: absolute;
  }

  #message {
    margin-top: 20px;
    font-size: 20px;
    color: #ff4d6d;
    font-weight: bold;
    min-height: 30px;
  }

  /* Floating Hearts */
  .heart {
    position: fixed;
    bottom: -20px;
    font-size: 20px;
    animation: floatUp linear infinite;
    opacity: 0.8;
  }

  @keyframes floatUp {
    from {
      transform: translateY(0);
      opacity: 1;
    }
    to {
      transform: translateY(-110vh);
      opacity: 0;
    }
  }
</style>
</head>

<body>

<audio id="bgMusic" loop>
  <source src="https://cdn.pixabay.com/audio/2023/02/14/audio_0b9a7c2e3c.mp3" type="audio/mpeg">
</audio>

<div class="card" id="card">
  <h1>Will you be my Valentine? 💖</h1>
  <div>
    <button id="yesBtn">YES 💘</button>
    <button id="noBtn">NO 😢</button>
  </div>
  <div id="message"></div>
</div>

<script>
  const yesBtn = document.getElementById("yesBtn");
  const noBtn = document.getElementById("noBtn");
  const message = document.getElementById("message");
  const music = document.getElementById("bgMusic");

  let yesScale = 1;
  let noCount = 0;

  const noMessages = [
    "Are you sure?",
    "Baby are you sure?",
    "Babyyyyyyy 🥺",
    "Just say yes baby 💕",
    "Baby pleaseeeeee 😭"
  ];

  // Start music on first interaction (mobile safe)
  document.body.addEventListener("click", () => {
    music.play().catch(() => {});
  }, { once: true });

  // NO button runs away
  noBtn.addEventListener("click", () => {
    yesScale += 0.25;
    yesBtn.style.transform = `scale(${yesScale})`;

    message.textContent = noMessages[noCount % noMessages.length];
    noCount++;

    const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
    const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);

    noBtn.style.left = `${x}px`;
    noBtn.style.top = `${y}px`;
  });

  // YES clicked
  yesBtn.addEventListener("click", () => {
    document.getElementById("card").innerHTML = `
      <h1>💖 I LOVE YOU 💖</h1>
      <p style="font-size:22px; color:#ff4d6d;">
        I love you so much my cutieee patootie Yana 💕
      </p>
    `;
  });

  // Floating hearts generator
  function createHeart() {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "💕";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (3 + Math.random() * 3) + "s";
    document.body.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 6000);
  }

  setInterval(createHeart, 400);
</script>

</body>
</html>
