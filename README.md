<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Full Screen Snake</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: #111;
      height: 100%;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    canvas {
      background: #000;
      border: 2px solid #fff;
      touch-action: none;
    }
    button {
      margin-top: 20px;
      padding: 15px 30px;
      font-size: 24px;
      background: #8BC34A; /* Light Green */
      color: white;
      border: none;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
      cursor: pointer;
      transition: background 0.3s ease;
    }
    button:hover {
      background: #7CB342; /* Slightly darker green on hover */
    }
  </style>
</head>
<body>

<canvas id="game"></canvas>
<button id="startBtn">Start</button>
<button id="retryBtn" style="display:none">Retry</button>

<script>
const canvas = document.getElementById('game');
const ctx = canvas.getContext('2d');
const retryBtn = document.getElementById('retryBtn');
const startBtn = document.getElementById('startBtn');

const box = 20;
let cols, rows;
let snake = [];
let direction = 'RIGHT';
let food;
let score = 0;
let highScore = localStorage.getItem("highScore") || 0;
let gameLoop;
let speed = 120;
let foodImages = ['🍎', '🥭', '🍇'];
let currentFoodImage = foodImages[0];

let eatSound = new Audio("https://www.soundjay.com/button/beep-07.wav");
let dieSound = new Audio("https://www.soundjay.com/button/beep-10.wav");

function resizeCanvas() {
  canvas.width = Math.floor(window.innerWidth / box) * box;
  canvas.height = Math.floor(window.innerHeight / box) * box;
  cols = canvas.width / box;
  rows = canvas.height / box;
}
resizeCanvas();
window.addEventListener('resize', () => {
  clearInterval(gameLoop);
  resizeCanvas();
  resetGame();
});

function resetGame() {
  snake = [
    { x: 5 * box, y: 5 * box },
    { x: 4 * box, y: 5 * box },
    { x: 3 * box, y: 5 * box }
  ];
  direction = 'RIGHT';
  food = randomFood();
  score = 0;
  retryBtn.style.display = 'none';
  startBtn.style.display = 'none';
  if (gameLoop) clearInterval(gameLoop);
  gameLoop = setInterval(draw, speed);
}

function randomFood() {
  currentFoodImage = foodImages[Math.floor(Math.random() * foodImages.length)];
  return {
    x: Math.floor(Math.random() * cols) * box,
    y: Math.floor(Math.random() * rows) * box
  };
}

function draw() {
  ctx.fillStyle = "black";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  for (let i = 0; i < snake.length; i++) {
    ctx.fillStyle = i === 0 ? "lime" : "green";
    ctx.fillRect(snake[i].x, snake[i].y, box, box);
  }

  const head = snake[0];
  ctx.fillStyle = "white";
  ctx.fillRect(head.x + 5, head.y + 5, 4, 4);
  ctx.fillRect(head.x + 11, head.y + 5, 4, 4);

  ctx.font = "20px Arial";
  ctx.fillText(currentFoodImage, food.x + 2, food.y + 18);

  let newX = head.x;
  let newY = head.y;
  if (direction === "LEFT") newX -= box;
  if (direction === "RIGHT") newX += box;
  if (direction === "UP") newY -= box;
  if (direction === "DOWN") newY += box;

  const newHead = { x: newX, y: newY };

  if (newX === food.x && newY === food.y) {
    snake.unshift(newHead);
    eatSound.play();
    food = randomFood();
    score++;
    if (score > highScore) {
      highScore = score;
      localStorage.setItem("highScore", highScore);
    }
  } else {
    snake.pop();
    snake.unshift(newHead);
  }

  if (
    newX < 0 || newX >= canvas.width ||
    newY < 0 || newY >= canvas.height ||
    collision(newHead, snake.slice(1))
  ) {
    clearInterval(gameLoop);
    dieSound.play();
    retryBtn.style.display = 'block';
    ctx.fillStyle = 'red';
    ctx.font = '24px Arial';
    ctx.fillText("Game Over!", canvas.width / 2 - 60, canvas.height / 2);
    return;
  }

  ctx.fillStyle = 'white';
  ctx.font = '16px Arial';
  ctx.fillText("Score: " + score, 10, 20);
  ctx.fillText("High Score: " + highScore, 10, 40);
}

function collision(head, arr) {
  return arr.some(segment => segment.x === head.x && segment.y === head.y);
}

document.addEventListener("keydown", e => {
  if (e.key === "ArrowLeft" && direction !== "RIGHT") direction = "LEFT";
  else if (e.key === "ArrowUp" && direction !== "DOWN") direction = "UP";
  else if (e.key === "ArrowRight" && direction !== "LEFT") direction = "RIGHT";
  else if (e.key === "ArrowDown" && direction !== "UP") direction = "DOWN";
});

let touchStartX = 0, touchStartY = 0;
canvas.addEventListener('touchstart', e => {
  touchStartX = e.touches[0].clientX;
  touchStartY = e.touches[0].clientY;
});
canvas.addEventListener('touchend', e => {
  const dx = e.changedTouches[0].clientX - touchStartX;
  const dy = e.changedTouches[0].clientY - touchStartY;
  if (Math.abs(dx) > Math.abs(dy)) {
    if (dx > 0 && direction !== "LEFT") direction = "RIGHT";
    else if (dx < 0 && direction !== "RIGHT") direction = "LEFT";
  } else {
    if (dy > 0 && direction !== "UP") direction = "DOWN";
    else if (dy < 0 && direction !== "DOWN") direction = "UP";
  }
});

startBtn.addEventListener("click", resetGame);
retryBtn.addEventListener("click", resetGame);
</script>

</body>
</html>
