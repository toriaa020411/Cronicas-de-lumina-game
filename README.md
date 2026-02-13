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