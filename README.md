<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Luz Lunar - Personalização</title>
<style>
    body, html {
        margin: 0;
        padding: 0;
        font-family: 'Arial', sans-serif;
        overflow: hidden;
    }

    /* Tela Inicial */
    #tela-inicial {
        width: 100vw;
        height: 100vh;
        background: url('floresta_particulas.png') center/cover no-repeat;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        color: white;
        text-align: center;
        position: relative;
    }

    #tela-inicial h1 {
        font-size: 6vw;
        margin-bottom: 20px;
        text-shadow: 2px 2px 10px #000;
    }

    #btn-comecar {
        padding: 15px 40px;
        font-size: 1.5rem;
        cursor: pointer;
        border: none;
        border-radius: 10px;
        background-color: rgba(100, 50, 200, 0.8);
        color: white;
        transition: all 0.3s;
    }

    #btn-comecar:hover {
        background-color: rgba(150, 100, 250, 0.9);
    }

    /* Tela de Personalização */
    #tela-personagem {
        width: 100vw;
        height: 100vh;
        background: url('entrada_escola.png') center/cover no-repeat;
        display: none;
        flex-direction: column;
        justify-content: flex-end;
        align-items: center;
        padding-bottom: 30px;
        position: relative;
    }

    /* Protagonista central */
    #personagem-preview {
        width: 300px;
        height: 500px;
        background: url('protagonista_base.png') center/contain no-repeat;
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        top: 50px;
    }

    /* Interface de customização */
    #customizacao {
        width: 90%;
        background: rgba(0,0,0,0.7);
        padding: 20px;
        border-radius: 15px;
        color: white;
        display: flex;
        flex-direction: column;
        align-items: center;
        z-index: 10;
    }

    .categoria {
        margin: 10px 0;
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    select {
        padding: 5px 10px;
        font-size: 1rem;
        border-radius: 5px;
    }

    .miniaturas {
        display: flex;
        flex-wrap: wrap;
        margin-top: 5px;
    }

    .miniatura {
        width: 50px;
        height: 50px;
        margin: 5px;
        border: 2px solid white;
        border-radius: 5px;
        cursor: pointer;
        background-size: cover;
    }

    #btn-confirmar {
        margin-top: 20px;
        padding: 10px 20px;
        font-size: 1.2rem;
        cursor: pointer;
        border: none;
        border-radius: 10px;
        background-color: purple;
        color: white;
        transition: 0.3s;
    }

    #btn-confirmar:hover {
        background-color: darkviolet;
    }

    /* Partículas animadas */
    .particula {
        position: absolute;
        width: 5px;
        height: 5px;
        background: white;
        border-radius: 50%;
        opacity: 0.8;
        animation: flutuar linear infinite;
    }

    @keyframes flutuar {
        0% { transform: translateY(0px); opacity:0.8; }
        50% { opacity:0.3; }
        100% { transform: translateY(-800px); opacity:0; }
    }
</style>
</head>
<body>

<!-- Tela Inicial -->
<div id="tela-inicial">
    <h1>Luz Lunar</h1>
    <button id="btn-comecar">Começar</button>
</div>

<!-- Tela de Personalização -->
<div id="tela-personagem">
    <div id="personagem-preview"></div>
    <div id="customizacao">
        <h2>Personalize sua protagonista</h2>

        <div class="categoria">
            <label>Roupas:</label>
            <select id="roupaSelect">
                <option>Uniforme Escolar</option>
                <option>Vestido Mágico</option>
                <option>Casual</option>
            </select>
        </div>

        <div class="categoria">
            <label>Penteado:</label>
            <select id="penteadoSelect">
                <option>Cabelo Longo</option>
                <option>Cabelo Curto</option>
                <option>Penteado Trançado</option>
            </select>
        </div>

        <div class="categoria">
            <label>Cor do cabelo:</label>
            <select id="cabeloSelect">
                <option>Castanho</option>
                <option>Preto</option>
                <option>Roxo</option>
                <option>Azul</option>
            </select>
        </div>

        <div class="categoria">
            <label>Tons de pele:</label>
            <select id="peleSelect">
                <option>Claro</option>
                <option>Moreno</option>
                <option>Escuro</option>
                <option>Rosa</option>
                <option>Azul</option>
            </select>
        </div>

        <div class="categoria">
            <label>Olhos:</label>
            <select id="olhosSelect">
                <option>Azuis</option>
                <option>Verdes</option>
                <option>Heterocromia Azul + Roxo</option>
                <option>Heterocromia Verde + Dourado</option>
            </select>
        </div>

        <button id="btn-confirmar">Pronto</button>
    </div>
</div>

<audio id="musica" loop>
    <source src="trilha_instrumental.mp3" type="audio/mpeg">
</audio>

<script>
    const btnComecar = document.getElementById('btn-comecar');
    const telaInicial = document.getElementById('tela-inicial');
    const telaPersonagem = document.getElementById('tela-personagem');
    const musica = document.getElementById('musica');
    const preview = document.getElementById('personagem-preview');

    const personagem = {};

    // Partículas mágicas na tela inicial
    for(let i=0;i<50;i++){
        let p = document.createElement('div');
        p.classList.add('particula');
        p.style.left = Math.random()*window.innerWidth+'px';
        p.style.top = Math.random()*window.innerHeight+'px';
        p.style.animationDuration = (5 + Math.random()*5)+'s';
        telaInicial.appendChild(p);
    }

    btnComecar.addEventListener('click', () => {
        telaInicial.style.display = 'none';
        telaPersonagem.style.display = 'flex';
        musica.play();
    });

    function atualizarPreview(){
        // Aqui você pode mudar o background do preview com base nas escolhas
        preview.style.background = `url('protagonista_${personagem.roupa||'base'}.png') center/contain no-repeat`;
    }

    document.getElementById('btn-confirmar').addEventListener('click', () => {
        personagem['roupa'] = document.getElementById('roupaSelect').value;
        personagem['penteado'] = document.getElementById('penteadoSelect').value;
        personagem['cabelo'] = document.getElementById('cabeloSelect').value;
        personagem['pele'] = document.getElementById('peleSelect').value;
        personagem['olhos'] = document.getElementById('olhosSelect').value;

        // Salva no localStorage
        localStorage.setItem('protagonista', JSON.stringify(personagem));

        alert("Personagem salva! Pronta para a aventura!");
        // Aqui você pode redirecionar para Capítulo 1
    });

    // Atualiza preview a cada mudança
    ['roupaSelect','penteadoSelect','cabeloSelect','peleSelect','olhosSelect'].forEach(id => {
        document.getElementById(id).addEventListener('change', ()=>{
            personagem[id.replace('Select','').toLowerCase()] = document.getElementById(id).value;
            atualizarPreview();
        });
    });

</script>

</body>
</html>