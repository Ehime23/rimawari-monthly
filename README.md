<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>利回り計算ツール（月額家賃）</title>
  <link rel="manifest" href="manifest.json">
  <link rel="apple-touch-icon" href="icons/icon-192x192.png">
  <meta name="theme-color" content="#ffffff">
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 2em;
      background-color: #f5f5f5;
    }
    h1 {
      font-size: 1.5em;
      margin-bottom: 1em;
    }
    input {
      display: block;
      margin-bottom: 1em;
      padding: 0.5em;
      width: 100%;
      font-size: 1em;
    }
    button {
      padding: 0.7em 1.2em;
      font-size: 1em;
      background-color: #007aff;
      color: white;
      border: none;
      border-radius: 5px;
    }
    #result {
      margin-top: 1.5em;
      font-size: 1.2em;
      color: #333;
    }
  </style>
</head>
<body>
  <h1>表面利回り計算ツール</h1>
  <label>物件価格（万円）</label>
  <input id="price" type="number" placeholder="例：2000">
  
  <label>月額家賃（万円）</label>
  <input id="monthlyIncome" type="number" placeholder="例：15">

  <button onclick="calculate()">計算する</button>
  
  <p id="result"></p>

  <script>
    function calculate() {
      const price = parseFloat(document.getElementById('price').value);
      const monthlyIncome = parseFloat(document.getElementById('monthlyIncome').value);

      if (isNaN(price) || isNaN(monthlyIncome) || price <= 0) {
        document.getElementById('result').textContent = "正しい数値を入力してください。";
        return;
      }

      const annualIncome = monthlyIncome * 12;
      const yield = (annualIncome / price * 100).toFixed(2);
      document.getElementById('result').textContent =
        `表面利回りは ${yield}%（年額家賃：${annualIncome}万円）です。`;
    }
  </script>
</body>
</html>
