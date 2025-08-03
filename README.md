# Bingo24

<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Slot Machine Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #1a1a1a;
      color: #fff;
    }
    .slot-machine {
      margin-top: 50px;
    }
    .reels {
      font-size: 60px;
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-bottom: 20px;
    }
    .wallet {
      margin: 20px 0;
      font-size: 20px;
    }
    button {
      padding: 10px 20px;
      font-size: 18px;
      background: #ffcc00;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .result {
      margin-top: 20px;
      font-size: 24px;
      color: #0f0;
    }
  </style>
</head>
<body>
  <div class="slot-machine">
    <div class="wallet">Balance: ₹1000</div>
    <div class="reels" id="reels">
      <span>🍒</span>
      <span>🍌</span>
      <span>🍉</span>
    </div>
    <button onclick="spin()">Spin (₹10)</button>
    <div class="result" id="result"></div>
  </div>  <script>
    const symbols = ['🍒', '🍌', '🍉', '🍎', '🍊'];
    let balance = 1000;

    function spin() {
      if (balance < 10) {
        alert("Not enough coins to spin!");
        return;
      }
      balance -= 10;

      const reelEls = document.querySelectorAll("#reels span");
      const resultEl = document.getElementById("result");
      let results = [];

      reelEls.forEach((reel, i) => {
        const symbol = symbols[Math.floor(Math.random() * symbols.length)];
        reel.textContent = symbol;
        results.push(symbol);
      });

      if (results[0] === results[1] && results[1] === results[2]) {
        balance += 100;
        resultEl.textContent = "Jackpot! You won ₹100!";
        resultEl.style.color = '#0f0';
      } else if (results[0] === results[1] || results[1] === results[2] || results[0] === results[2]) {
        balance += 30;
        resultEl.textContent = "Nice! You won ₹30!";
        resultEl.style.color = '#ff0';
      } else {
        resultEl.textContent = "No match. Try again!";
        resultEl.style.color = '#f00';
      }

      document.querySelector(".wallet").textContent = `Balance: ₹${balance}`;
    }
  </script></body>
</html>
