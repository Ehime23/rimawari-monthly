
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>宮里式計算機</title>
  <link href="https://fonts.googleapis.com/css2?family=Zen+Maru+Gothic:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    body {
      font-family: 'Zen Maru Gothic', sans-serif;
      background-color: #fff0f5;
      padding: 2em;
      color: #333;
    }

    h1 {
      text-align: center;
      font-size: 1.8em;
      margin-bottom: 1em;
    }

    .container {
      max-width: 400px;
      margin: 0 auto;
      background: #fff;
      padding: 2em;
      border-radius: 15px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    label {
      display: block;
      margin-bottom: 0.3em;
      font-weight: bold;
    }

    input {
      width: 100%;
      padding: 0.6em;
      margin-bottom: 1.2em;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 1em;
    }

    button {
      width: 100%;
      padding: 0.8em;
      font-size: 1em;
      background-color: #87cefa;
      color: white;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background-color: #6ab7e5;
    }

    #result {
      margin-top: 1.5em;
      font-size: 1.2em;
      text-align: center;
      color: #444;
    }

    header, h1:first-of-type:has(a[href*="github.io"]) {
      display: none !important;
    }
  </style>
</head>
<body>
  <h1>宮里式計算機</h1>
  <div class="container">
    <label for="price">物件価格（万円）</label>
    <input id="price" type="number" placeholder="例：2000" />

    <label for="monthlyIncome">月額家賃（万円）</label>
    <input id="monthlyIncome" type="number" placeholder="例：15" />

    <button onclick="calculate()">計算する</button>
    <p id="result"></p>
  </div>

  <script>
    function calculate() {
      const price = parseFloat(document.getElementById("price").value);
      const monthlyIncome = parseFloat(document.getElementById("monthlyIncome").value);
      if (isNaN(price) || isNaN(monthlyIncome) || price <= 0) {
        document.getElementById("result").textContent = "正しい数値を入力してください。";
        return;
      }
      const annualIncome = monthlyIncome * 12;
      const yield = (annualIncome / price * 100).toFixed(2);
      document.getElementById("result").textContent =
        `表面利回りは ${yield}%（年額家賃：${annualIncome}万円）です。`;
    }
  </script>
</body>
</html>
