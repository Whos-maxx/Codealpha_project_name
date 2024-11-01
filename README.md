# Codealpha_project_name
html

Copy code

<!DOCTYPE html>

<html lang="en">

<head>

  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Simple Calculator</title>

  <style>

    /* Calculator styling */

    body {

      display: flex;

      justify-content: center;

      align-items: center;

      height: 100vh;

      margin: 0;

      font-family: Arial, sans-serif;

      background-color: #f0f0f0;

    }

    .calculator {

      width: 300px;

      background-color: #333;

      border-radius: 8px;

      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);

      padding: 20px;

    }

    .display {

      width: 100%;

      height: 60px;

      background-color: #222;

      color: #fff;

      text-align: right;

      font-size: 24px;

      padding: 10px;

      border-radius: 4px;

      margin-bottom: 20px;

      box-sizing: border-box;

    }

    .buttons {

      display: grid;

      grid-template-columns: repeat(4, 1fr);

      gap: 10px;

    }

    .button {

      width: 100%;

      padding: 20px;

      font-size: 18px;

      background-color: #555;

      color: white;

      border: none;

      border-radius: 4px;

      cursor: pointer;

      transition: background-color 0.3s;

    }

    .button:hover {

      background-color: #777;

    }

    .button.operation {

      background-color: #ff9500;

    }

    .button.operation:hover {

      background-color: #ffb64d;

    }

  </style>

</head>

<body>



<div class="calculator">

  <div id="display" class="display">0</div>

  <div class="buttons">

    <button class="button" onclick="clearDisplay()">C</button>

    <button class="button" onclick="appendNumber('%')">%</button>

    <button class="button" onclick="appendOperator('/')">÷</button>

    <button class="button operation" onclick="appendOperator('*')">×</button>
    <button class="button" onclick="appendNumber('7')">7</button>

    <button class="button" onclick="appendNumber('8')">8</button>

    <button class="button" onclick="appendNumber('9')">9</button>

    <button class="button operation" onclick="appendOperator('-')">−</button>
    <button class="button" onclick="appendNumber('4')">4</button>

    <button class="button" onclick="appendNumber('5')">5</button>

    <button class="button" onclick="appendNumber('6')">6</button>

    <button class="button operation" onclick="appendOperator('+')">+</button>
    <button class="button" onclick="appendNumber('1')">1</button>

    <button class="button" onclick="appendNumber('2')">2</button>

    <button class="button" onclick="appendNumber('3')">3</button>

    <button class="button operation" onclick="calculate()">=</button>
    <button class="button" onclick="appendNumber('0')">0</button>

    <button class="button" onclick="appendNumber('.')">.</button>

  </div>
</div>
<script>

  let displayElement = document.getElementById("display");

  let currentInput = "0";

  let operator = "";

  let previousInput = "";
  // Display helper functions

  function updateDisplay(value) {

    displayElement.innerText = value;

  }
  function clearDisplay() {

    currentInput = "0";

    operator = "";

    previousInput = "";

    updateDisplay(currentInput);

  }
  function appendNumber(number) {

    if (currentInput === "0") {

      currentInput = number;

    } else {

      currentInput += number;

    }

    updateDisplay(currentInput);

  }
  function appendOperator(op) {

    if (currentInput === "") return;
    if (operator !== "") {
      calculate();
    }
    operator = op;

    previousInput = currentInput;

    currentInput = "";

  }
  function calculate() {

    let result;

    const prev = parseFloat(previousInput);

    const current = parseFloat(currentInput);

    if (isNaN(prev) || isNaN(current)) return;



    switch (operator) {

      case "+":

        result = prev + current;

        break;

      case "-":

        result = prev - current;

        break;

      case "*":

        result = prev * current;

        break;

      case "/":

        result = prev / current;

        break;

      default:

        return;

    }
    currentInput = result.toString();

    operator = "";

    previousInput = "";

    updateDisplay(currentInput);

  }
</script>
</body>

</html>
