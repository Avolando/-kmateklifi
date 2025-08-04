<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <title>Senin için bir soru var...</title>
  <style>
    body {
      margin: 0;
      background: black;
      color: white;
      font-family: 'Arial', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
    }

    #intro, #questionBox {
      text-align: center;
      opacity: 0;
      animation: fadeIn 2s forwards;
    }

    #intro button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 1.2em;
      background-color: pink;
      color: black;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.3s;
    }

    #questionBox {
      display: none;
      flex-direction: column;
      align-items: center;
    }

    .heart {
      font-size: 60px;
      animation: beat 1s infinite;
      margin-bottom: 10px;
    }

    .question-text {
      font-size: 1.6em;
      margin: 15px 20px;
      max-width: 90%;
    }

    button.yes, button.no {
      margin: 10px;
      padding: 10px 20px;
      font-size: 1.2em;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.3s;
    }

    .yes { background-color: pink; color: black; }
    .no { background-color: gray; color: white; }

    /* Titreme animasyonu */
    @keyframes shake {
      0% { transform: translateX(0); }
      25% { transform: translateX(-5px); }
      50% { transform: translateX(5px); }
      75% { transform: translateX(-3px); }
      100% { transform: translateX(0); }
    }

    .shake {
      animation: shake 0.3s ease-in-out;
      animation-iteration-count: 4;
    }

    #noMessage {
      display: none;
      margin-top: 15px;
      font-size: 1.2em;
      color: pink;
      transition: opacity 0.5s ease;
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    @keyframes beat {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.2); }
    }
  </style>
</head>
<body>

  <div id="intro">
    <h1>Sana söylemek istediğim bir şey var...</h1>
    <button onclick="showQuestion()">Devam et</button>
  </div>

  <div class="question" id="questionBox">
    <div class="heart">❤️</div>
    <div class="question-text">
      Kalbim seni tanıdığından beri daha hızlı atıyor...<br>
      Benimle bir yola çıkar mısın?
    </div>
    <button class="yes" onclick="accept()">Evet</button>
    <button class="no" id="noBtn" onclick="shakeNo()">Hayır</button>
    <div id="noMessage">Hayır deme şansın yok, hayırdır :)</div>
  </div>

  <script>
    function showQuestion() {
      document.getElementById("intro").style.display = "none";
      document.getElementById("questionBox").style.display = "flex";
    }

    function accept() {
      document.body.innerHTML = `
        <div style="text-align:center; padding:50px;">
          <h1 style="color:pink;">Yaa cidden mi?! 🥹💖</h1>
          <p>Hazırlan, çünkü artık birlikteyiz! 💑</p>
          <div style="font-size:80px;">🎉💘🎉</div>
        </div>
      `;
    }

    function shakeNo() {
      const noBtn = document.getElementById("noBtn");
      const msg = document.getElementById("noMessage");

      noBtn.classList.add("shake");
      msg.style.display = "block";

      setTimeout(() => {
        noBtn.classList.remove("shake");
      }, 1200);
    }
  </script>

</body>
</html>
