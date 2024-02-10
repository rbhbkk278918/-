<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Генератор сложных уравнений</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

<div>
  <h1>Генератор сложных уравнений</h1>
  <p id="equation"></p>
  <button onclick="generateEquation()">Сгенерировать уравнение</button>
</div>

<script src="script.js"></script>

<script>
  function generateEquation() {
    const operations = ['+', '-', '*', '/' , "____  "            ]; 
    const randomOperation = () => operations[Math.floor(Math.random() * operations.length)];
    const randomOperand = () => {
      const min = -200;
      const max = 200;
      return Math.floor(Math.random() * (max - min + 1)) + min;
    };

    const numberOfOperands = Math.floor(Math.random() * 8) + 2; // От 2 до 8 операций
    let equation = '';

    for (let i = 0; i < numberOfOperands; i++) {
      if (i > 0) {
        equation += ` ${randomOperation()} `;
      }

      if (i !== numberOfOperands - 1) {
        equation += '(';
      }

      equation += randomOperand();

      if (i !== 0) {
        equation += ')';
      }
    }

    document.getElementById('equation').textContent = `Уравнение: ${equation}`;
  }
</script>

</body>
</html>
