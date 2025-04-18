<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Snake Game</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: #111;
      height: 100%;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
    }
    canvas {
      background: #000;
      border: 2px solid #fff;
      touch-action: none;
    }
    .game-button {
      position: absolute;
      top: 60%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 12px 30px;
      font-size: 20px;
      background-color: #4caf50;
      color: white;
      border: none;
      border-radius: 10px;
      display: none;
    }
  </style>
</head>
<body>

<canvas id="game"></canvas>
<button id="startBtn" class="game-button">Start</button>
<button id="retryBtn" class="game-button">Retry</button>

<script>
const canvas = document.getElementById('game');
const ctx = canvas.getContext('2d');
const retryBtn = document.getElementById('retryBtn');
const startBtn = document.getElementById('startBtn');

let box, cols, rows;
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
  const width = window.innerWidth * 0.9;
  const height = window.innerHeight * 0.9;
  canvas.width = width;
  canvas.height = height;

  cols = Math.floor(width / 20);
  rows = Math.floor(height / 20);
  box = Math.floor(width / cols);
}
resizeCanvas();

window.addEventListener('resize', () => {
  clearInterval(gameLoop);
  resizeCanvas();
  showStart();
});

function randomFood() {
  currentFoodImage = foodImages[Math.floor(Math.random() * foodImages.length)];
  return {
    x: Math.floor(Math.random() * cols) * box,
    y: Math.floor(Math.random() * rows) * box
  };
}

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
  gameLoop = setInterval(draw, speed);
}

function draw() {
  ctx.fillStyle = "black";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  // Snake
  for (let i = 0; i < snake.length; i++) {
    ctx.fillStyle = i === 0 ? "lime" : "green";
    ctx.fillRect(snake[i].x, snake[i].y, box, box);
  }

  // Eyes
  const head = snake[0];
  ctx.fillStyle = "white";
  ctx.fillRect(head.x + box * 0.25, head.y + box * 0.25, box * 0.15, box * 0.15);
  ctx.fillRect(head.x + box * 0.6, head.y + box * 0.25, box * 0.15, box * 0.15);

  // Food
  ctx.font = `${box}px Arial`;
  ctx.fillText(currentFoodImage, food.x + 2, food.y + box - 2);

  // Move
  let newX = head.x;
  let newY = head.y;
  if (direction === "LEFT") newX -= box;
  if (direction === "RIGHT") newX += box;
  if (direction === "UP") newY -= box;
  if (direction === "DOWN") newY += box;

  const newHead = { x: newX, y: newY };

  // Eat food
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

  // Collision
  if (
    newX < 0 || newX >= canvas.width ||
    newY < 0 || newY >= canvas.height ||
    collision(newHead, snake.slice(1))
  ) {
    clearInterval(gameLoop);
    dieSound.play();
    ctx.fillStyle = 'red';
    ctx.font = `${Math.floor(box * 1.2)}px Arial`;
    ctx.fillText("Game Over!", canvas.width / 2 - box * 3, canvas.height / 2);
    retryBtn.style.display = 'block';
    return;
  }

  // Score
  ctx.fillStyle = 'white';
  ctx.font = `${Math.floor(box * 0.8)}px Arial`;
  ctx.fillText("Score: " + score, 10, box);
  ctx.fillText("High Score: " + highScore, 10, box * 2);
}

function collision(head, arr) {
  return arr.some(segment => segment.x === head.x && segment.y === head.y);
}

// Controls
document.addEventListener("keydown", e => {
  if (e.key === "ArrowLeft" && direction !== "RIGHT") direction = "LEFT";
  else if (e.key === "ArrowUp" && direction !== "DOWN") direction = "UP";
  else if (e.key === "ArrowRight" && direction !== "LEFT") direction = "RIGHT";
  else if (e.key === "ArrowDown" && direction !== "UP") direction = "DOWN";
});

// Touch controls
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

// Buttons
startBtn.addEventListener("click", () => {
  startBtn.style.display = 'none';
  resetGame();
});
retryBtn.addEventListener("click", () => {
  retryBtn.style.display = 'none';
  resetGame();
});

function showStart() {
  startBtn.style.display = 'block';
}
showStart();
</script>

</body>
</html>
