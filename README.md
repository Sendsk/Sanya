<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Тапалка с какашками</title>
  <style>
    /* Анимация переливающегося фона */
    body {
      margin: 0;
      padding: 0;
      font-family: 'Courier New', monospace;
      background: linear-gradient(-45deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee);
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
      text-align: center;
      overflow: hidden;
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      user-select: none;
    }

    @keyframes gradientBG {
      0% {background-position: 0% 50%;}
      50% {background-position: 100% 50%;}
      100% {background-position: 0% 50%;}
    }

    /* Счётчик */
    #score-box {
      background-color: black;
      color: white;
      padding: 15px 30px;
      font-size: 24px;
      border-radius: 8px;
      margin-top: 20px;
      font-family: 'Press Start 2P', cursive;
      letter-spacing: 1px;
      box-shadow: 0 0 10px rgba(0,0,0,0.5);
    }

    /* Контейнер для монетки */
    #coin-container {
      position: relative;
      width: 100%;
      flex-grow: 1;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    /* Монетка */
    #coin {
      width: 60vmin;
      height: 60vmin;
      cursor: pointer;
      transition: transform 0.1s ease;
      border-radius: 50%; /* Делает монетку круглой */
      z-index: 2;
    }

    /* Какашка */
    .poop {
      position: absolute;
      top: -50px; /* Появляются сверху */
      font-size: 32px;
      animation: fallRandom 1.5s ease-out forwards;
      pointer-events: none;
      user-select: none;
    }

    @keyframes fallRandom {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }

    /* Подключение пиксельного шрифта */
    @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');
  </style>
</head>
<body>

  <!-- Счётчик -->
  <div id="score-box">Счёт: 0</div>

  <!-- Контейнер с монеткой -->
  <div id="coin-container">
    <!-- ТУТ НАХОДИТСЯ МОНЕТКА -->
    <!-- ЗАМЕНИ src="monetka.png" НА СВОЮ КАРТИНКУ -->
    <img id="coin" src="C:\Users\egorf\OneDrive\Desktop\photo_2025-06-13_18-34-48.jpg" alt="Саня гей">
  </div>

  <script>
    let score = 0;
    const coin = document.getElementById('coin');
    const scoreBox = document.getElementById('score-box');
    const container = document.getElementById('coin-container');

    // Функция создания нескольких какашек
    function createPoops(count = 5) {
      for (let i = 0; i < count; i++) {
        const poop = document.createElement('div');
        poop.className = 'poop';
        poop.textContent = '💩';

        // Случайная позиция по горизонтали
        const randomX = Math.random() * window.innerWidth;

        poop.style.left = ${randomX}px;
        container.appendChild(poop);

        // Удаление после анимации
        setTimeout(() => {
          poop.remove();
        }, 1500);
      }
    }

    // Обработчик клика
    coin.addEventListener('click', () => {
      score++;
      scoreBox.textContent = 'Счёт: ' + score;

      // Анимация нажатия
      coin.style.transform = 'scale(0.9)';
      setTimeout(() => {
        coin.style.transform = 'scale(1)';
      }, 100);

      // Создаём много какашек
      createPoops(7); // Можно менять количество
    });
  </script>

</body>
</html># Sanya
