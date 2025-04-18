<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Dino Game</title>
  <style>
    body {
      background: #f4f4f4;
      font-family: sans-serif;
      overflow: hidden;
    }

    #game {
      width: 100%;
      height: 200px;
      background-color: #fff;
      border: 2px solid #000;
      position: relative;
      overflow: hidden;
    }

    #dino {
      width: 40px;
      height: 40px;
      background-color: green;
      position: absolute;
      bottom: 0;
      left: 50px;
    }

    #cactus {
      width: 20px;
      height: 40px;
      background-color: red;
      position: absolute;
      bottom: 0;
      left: 100%;
      animation: moveCactus 2s infinite linear;
    }

    @keyframes moveCactus {
      0% {
        left: 100%;
      }
      100% {
        left: -20px;
      }
    }

    .jump {
      animation: jump 0.5s ease-out;
    }

    @keyframes jump {
      0% { bottom: 0; }
      50% { bottom: 80px; }
      100% { bottom: 0; }
    }
  </style>
</head>
<body>

<h2>Chrome Dino Game (Simple)</h2>
<div id="game">
  <div id="dino"></div>
  <div id="cactus"></div>
</div>

<script>
  const dino = document.getElementById("dino");
  const cactus = document.getElementById("cactus");

  document.addEventListener("keydown", function(event) {
    if (event.code === "Space" || event.key === " ") {
      if (!dino.classList.contains("jump")) {
        dino.classList.add("jump");
        setTimeout(() => {
          dino.classList.remove("jump");
        }, 500);
      }
    }
  });

  setInterval(function () {
    const dinoTop = parseInt(window.getComputedStyle(dino).getPropertyValue("bottom"));
    const cactusLeft = parseInt(window.getComputedStyle(cactus).getPropertyValue("left"));

    if (cactusLeft < 90 && cactusLeft > 40 && dinoTop < 40) {
      alert("Game Over!");
    }
  }, 10);
</script>

</body>
</html>
