# calculator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(135deg, #1e3c72, #2a5298);
      font-family: Arial, sans-serif;
    }

    .calculator {
      width: 320px;
      background: #222;
      border-radius: 15px;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.6);
      overflow: hidden;
    }

    .display {
      background: #111;
      color: #0f0;
      font-size: 2.5rem;
      text-align: right;
      padding: 20px;
      height: 80px;
      box-sizing: border-box;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
    }

    button {
      padding: 20px;
      font-size: 1.2rem;
      border: none;
      outline: none;
      cursor: pointer;
      background: #333;
      color: white;
      transition: 0.2s;
    }

    button:hover {
      background: #444;
    }

    .operator {
      background: #ff9500;
      color: #fff;
    }

    .operator:hover {
      background: #e08900;
    }

    .equal {
      grid-column: span 2;
      background: #28a745;
    }

    .equal:hover {
      background: #218838;
    }

    .clear {
      background: #dc3545;
    }

    .clear:hover {
      background: #b52a37;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button class="clear" onclick="clearDisplay()">C</button>
      <button onclick="appendValue('%')">%</button>
      <button onclick="backspace()">⌫</button>
      <button class="operator" onclick="appendValue('/')">÷</button>

      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button class="operator" onclick="appendValue('*')">×</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button class="operator" onclick="appendValue('-')">−</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button class="operator" onclick="appendValue('+')">+</button>

      <button onclick="appendValue('0')">0</button>
      <button onclick="appendValue('.')">.</button>
      <button class="equal" onclick="calculate()">=</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");

    function appendValue(value) {
      if (display.innerText === "0") {
        display.innerText = value;
      } else {
        display.innerText += value;
      }
    }

    function clearDisplay() {
      display.innerText = "0";
    }

    function backspace() {
      display.innerText = display.innerText.slice(0, -1) || "0";
    }

    function calculate() {
      try {
        display.innerText = eval(display.innerText.replace("÷", "/").replace("×", "*"));
      } catch {
        display.innerText = "Error";
      }
    }
  </script>
</body>
</html>
