<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Случайный цвет кнопки</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(135deg, #f6d365, #fda085);
            font-family: Arial, sans-serif;
        }

        #counter {
            font-size: 48px;
            font-weight: bold;
            margin-bottom: 20px;
        }

        #buttonContainer {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }

        #colorBtn, #autoClickerBtn {
            padding: 20px 40px;
            font-size: 24px;
            border: none;
            border-radius: 8px;
            background-color: #fff;
            color: #333;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
            margin: 0 10px;
        }

        #colorBtn:hover, #autoClickerBtn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }
    </style>
</head>
<body>
    <div id="counter">0</div>
    <div id="buttonContainer">
        <button id="colorBtn">Тыкни</button>
        <button id="autoClickerBtn">Устал?</button>
    </div>
    <script>
        const button = document.getElementById('colorBtn');
        const autoClickerBtn = document.getElementById('autoClickerBtn');
        const counterElement = document.getElementById('counter');
        let counter = 0;
        let autoClicker;
        let isAutoClickerActive = false;

        button.addEventListener('click', changeColor);
        autoClickerBtn.addEventListener('click', toggleAutoClicker);

        function changeColor() {
            const randomColor = '#' + Math.floor(Math.random() * 16777215).toString(16);
            button.style.backgroundColor = randomColor;
            counter++;
            counterElement.textContent = counter;
        }

        function startAutoClicker() {
            autoClicker = setInterval(changeColor, 500);
            autoClickerBtn.textContent = "Выключить?";
            isAutoClickerActive = true;
        }

        function stopAutoClicker() {
            clearInterval(autoClicker);
            autoClickerBtn.textContent = "Устал?";
            isAutoClickerActive = false;
        }

        function toggleAutoClicker() {
            if (isAutoClickerActive) {
                stopAutoClicker();
            } else {
                startAutoClicker();
            }
        }
    </script>
</body>
</html>
