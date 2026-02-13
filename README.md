# Cronicas-de-lumina-game
Jogo fisica
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Crônicas de Lúmina</title>
<style>
body {
    margin:0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(to bottom, #1a1a2e, #16213e);
    color: white;
    text-align:center;
}

#game {
    padding:20px;
}

.scene {
    min-height:200px;
    padding:20px;
    border-radius:15px;
    background: rgba(255,255,255,0.05);
    box-shadow: 0 0 20px rgba(255,255,255,0.1);
    margin-bottom:20px;
}

button {
    padding:10px 20px;
    margin:10px;
    border:none;
    border-radius:10px;
    background: linear-gradient(45deg, #ff4e88, #6a5acd);
    color:white;
    font-size:16px;
}

button:hover {
    opacity:0.8;
}

.stats {
    display:flex;
    justify-content:space-around;
    margin-bottom:15px;
}

.bar {
    background:rgba(255,255,255,0.1);
    border-radius:10px;
    padding:5px;
}
</style>
</head>

<body>

<div id="game">

<h1>🌙 Crônicas de Lúmina</h1>

<div class="stats">
<div class="bar">🔷 Lógica: <span id="math">0</span></div>
<div class="bar">🔥 Alquimia: <span id="chem">0</span></div>
<div class="bar">⚡ Leis: <span id="phys">0</span></div>
<div class="bar">💘 Romance: <span id="love">0</span></div>
</div>

<div class="scene" id="sceneText"></div>

<div id="choices"></div>

</div>

<script>
let stats = {
math:0,
chem:0,
phys:0,
love:0
};

function updateStats(){
document.getElementById("math").innerText = stats.math;
document.getElementById("chem").innerText = stats.chem;
document.getElementById("phys").innerText = stats.phys;
document.getElementById("love").innerText = stats.love;
localStorage.setItem("luminaSave", JSON.stringify(stats));
}

function loadGame(){
let save = localStorage.getItem("luminaSave");
if(save){
stats = JSON.parse(save);
updateStats();
}
}

function showScene(text, options){
document.getElementById("sceneText").innerHTML = text;
let choicesDiv = document.getElementById("choices");
choicesDiv.innerHTML = "";
options.forEach(option => {
let btn = document.createElement("button");
btn.innerText = option.text;
btn.onclick = option.action;
choicesDiv.appendChild(btn);
});
}

function startGame(){
showScene(
"🏰 Você chega à Academia Arcana de Lúmina.<br><br>Um jovem de olhar intenso observa você. Ele cruza os braços.<br><br>'Então… você é a nova Guardiã?'",
[
{text:"Responder confiante", action:()=>{
stats.love +=1;
updateStats();
academyTest();
}},
{text:"Responder tímida", action:()=>{
academyTest();
}}
]
);
}

function academyTest(){
showScene(
"📜 Primeira Prova: O Portal Matemático.<br><br>Se 3 cristais geram 15 unidades de energia, quantos cristais são necessários para gerar 30?",
[
{text:"5 cristais", action:wrong},
{text:"6 cristais", action:correctMath},
{text:"10 cristais", action:wrong}
]
);
}

function correctMath(){
stats.math +=2;
stats.love +=1;
updateStats();
showScene(
"✨ Correto! Cada cristal gera 5 unidades.<br><br>Ele sorri levemente. 'Impressionante…'",
[
{text:"Continuar", action:alchemyTest}
]
);
}

function alchemyTest(){
showScene(
"🔥 Aula de Alquimia.<br><br>Você mistura dois elementos. Quando combinados, produzem calor e luz.<br><br>Isso é um exemplo de:",
[
{text:"Reação química", action:correctChem},
{text:"Mudança física", action:wrong}
]
);
}

function correctChem(){
stats.chem +=2;
stats.love +=1;
updateStats();
showScene(
"🌟 Correto! Uma nova substância foi formada.<br><br>Ele se aproxima: 'Você aprende rápido demais... perigoso.'",
[
{text:"Ir para a missão externa", action:physicsMission}
]
);
}

function physicsMission(){
showScene(
"🌌 Missão fora da Academia.<br><br>Uma ponte mágica está instável.<br><br>Se um objeto cai, a força que o puxa é:",
[
{text:"Magia invisível", action:wrong},
{text:"Gravidade", action:correctPhys}
]
);
}

function correctPhys(){
stats.phys +=2;
stats.love +=2;
updateStats();
showScene(
"⚡ Correto! A gravidade mantém tudo no lugar.<br><br>Ele segura sua mão para atravessar a ponte.<br><br>'Talvez você seja mesmo a escolhida.'",
[
{text:"Salvar e continuar", action:endGame}
]
);
}

function wrong(){
showScene(
"❌ Algo falhou. Mas tudo bem, aprender é parte da jornada.<br><br>Tente novamente.",
[
{text:"Tentar de novo", action:academyTest}
]
);
}

function endGame(){
showScene(
"🌙 Fim do Capítulo 1.<br><br>Você evoluiu como Guardiã.<br><br>Seu vínculo com ele cresce lentamente...<br><br>Continua...",
[
{text:"Recomeçar", action:startGame}
]
);
}

loadGame();
startGame();
</script>

</body>
</html>
