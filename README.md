<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Luz Lunar</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>

  <!-- TELA INICIAL -->
  <div id="telaInicial" class="screen active">
    <div class="background-layer"></div>
    <div class="ui-layer">
      <h1>Luz Lunar</h1>
      <button onclick="iniciarJogo()">Novo Jogo</button>
    </div>
  </div>

  <!-- TELA PERSONALIZAÇÃO -->
  <div id="telaCriacao" class="screen">

    <div class="personagem">

      <img id="base" class="layer">
      <img id="pele" class="layer">
      <img id="manchas" class="layer">
      <img id="roupa" class="layer">
      <img id="olhos" class="layer">
      <img id="sobrancelha" class="layer">
      <img id="boca" class="layer">
      <img id="cabelo" class="layer">

    </div>

    <div class="menu-opcoes">
      <button onclick="mudarCabelo('longo_azul')">Cabelo Azul</button>
      <button onclick="mudarOlhos('heterocromia_azul_roxo')">Heterocromia</button>
      <button onclick="toggleManchas()">Manchas</button>
      <button onclick="salvarPersonagem()">Pronto</button>
    </div>

  </div>

  <script src="js/character.js"></script>
  <script src="js/saveSystem.js"></script>
  <script src="js/game.js"></script>

</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Luz Lunar</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>

  <!-- TELA INICIAL -->
  <div id="telaInicial" class="screen active">
    <div class="background-layer"></div>
    <div class="ui-layer">
      <h1>Luz Lunar</h1>
      <button onclick="iniciarJogo()">Novo Jogo</button>
    </div>
  </div>

  <!-- TELA PERSONALIZAÇÃO -->
  <div id="telaCriacao" class="screen">

    <div class="personagem">

      <img id="base" class="layer">
      <img id="pele" class="layer">
      <img id="manchas" class="layer">
      <img id="roupa" class="layer">
      <img id="olhos" class="layer">
      <img id="sobrancelha" class="layer">
      <img id="boca" class="layer">
      <img id="cabelo" class="layer">

    </div>

    <div class="menu-opcoes">
      <button onclick="mudarCabelo('longo_azul')">Cabelo Azul</button>
      <button onclick="mudarOlhos('heterocromia_azul_roxo')">Heterocromia</button>
      <button onclick="toggleManchas()">Manchas</button>
      <button onclick="salvarPersonagem()">Pronto</button>
    </div>

  </div>

  <script src="js/character.js"></script>
  <script src="js/saveSystem.js"></script>
  <script src="js/game.js"></script>

</body>
</html>
body {
  margin: 0;
  font-family: serif;
  background-color: #0f0f1a;
  color: white;
}

.screen {
  display: none;
  height: 100vh;
  position: relative;
}

.screen.active {
  display: block;
}

.personagem {
  position: relative;
  width: 400px;
  margin: auto;
}

.layer {
  position: absolute;
  width: 100%;
}

.menu-opcoes {
  position: absolute;
  right: 50px;
  top: 100px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

function mudarCabelo(tipo) {
  document.getElementById("cabelo").src =
    `assets/character/hair/${tipo}.png`;
}

function mudarOlhos(tipo) {
  document.getElementById("olhos").src =
    `assets/character/eyes/${tipo}.png`;
}

function toggleManchas() {
  let manchas = document.getElementById("manchas");

  if (manchas.src.includes("manchas_pele.png")) {
    manchas.src = "";
  } else {
    manchas.src = "assets/character/extras/manchas_pele.png";
  }
}
function salvarPersonagem() {

  const personagem = {
    cabelo: document.getElementById("cabelo").src,
    olhos: document.getElementById("olhos").src,
    manchas: document.getElementById("manchas").src
  };

  localStorage.setItem("personagem", JSON.stringify(personagem));

  alert("Personagem salva com sucesso!");
}
