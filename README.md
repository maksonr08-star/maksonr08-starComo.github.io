<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>2 meses 💜</title>

<style>
body {
  margin: 0;
  font-family: Arial;
  background: linear-gradient(135deg, #0d001a, #4b0082);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  text-align: center;
}

/* botão inicial */
button {
  padding: 15px 30px;
  border-radius: 30px;
  border: none;
  background: white;
  color: #4b0082;
  font-size: 16px;
  cursor: pointer;
}

/* botão música */
#btnMusica {
  position: absolute;
  top: 20px;
  right: 20px;
  padding: 8px 15px;
  font-size: 12px;
  background: rgba(255,255,255,0.2);
  color: white;
  border-radius: 20px;
}

/* conteúdo */
.main {
  display: none;
  max-width: 340px;
}

.nome {
  font-size: 26px;
  margin-bottom: 10px;
  color: #ff66cc;
}

/* FOTO */
.foto {
  width: 160px;
  height: 160px;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid #ff66cc;
  margin: 10px auto;
  display: block;
  box-shadow: 0 0 20px #ff66cc;
  animation: aparecer 2s ease;
}

@keyframes aparecer {
  from { opacity: 0; transform: scale(0.7); }
  to { opacity: 1; transform: scale(1); }
}

/* texto */
.texto {
  margin-top: 15px;
  line-height: 1.7;
  min-height: 250px;
  border-right: 2px solid white;
  white-space: pre-line;
}

/* corações */
.heart {
  position: absolute;
  color: #ff66cc;
  animation: subir 5s linear infinite;
}

@keyframes subir {
  0% { transform: translateY(100vh); opacity: 1; }
  100% { transform: translateY(-10vh); opacity: 0; }
}
</style>
</head>

<body>

<button id="btnMusica" onclick="toggleMusica()">🔇 Música</button>

<div id="inicio">
  <button onclick="iniciar()">Clica aqui… 💜</button>
</div>

<div id="main" class="main">
  <div class="nome">Ana Caroline 💜</div>

  <!-- FOTO -->
  <img src="foto.jpg" class="foto">

  <div id="texto" class="texto"></div>
</div>

<audio id="musica" src="musica.mp3"></audio>

<script>
const mensagem = `Já vão fazer 2 meses…
e, quanto mais eu penso nisso,
mais eu percebo que não é sobre o tempo —
é sobre o que você se tornou dentro dele.

Porque você não chegou fazendo barulho…
você foi ficando.
Devagar, sem pressa…
e quando eu vi, já tinha tomado um espaço em mim
que antes era vazio.

E é estranho…
porque eu não sei explicar exatamente quando começou,
só sei que, de repente,
era você em todos os meus pensamentos mais calmos.

Não é só o seu sorriso,
nem só o seu jeito fofo…
é o que você causa em mim.

É essa paz que aparece
mesmo quando o resto tá bagunçado.
É essa leveza que você traz
sem nem perceber.

Com você, tudo parece mais simples.
Mais verdadeiro.

E, mesmo quando eu fico quieto,
mesmo quando eu não falo nada…
é em você que eu penso.

É você que eu procuro,
mesmo sem dizer.

E isso…
não é algo qualquer.

Eu nunca fui de sentir assim com facilidade,
mas com você foi diferente.

Foi real.

E talvez eu não saiba transformar tudo isso
nas palavras mais bonitas do mundo…
mas sei que é sincero.

Porque não é algo que passa.
Não é algo que eu inventei.

É algo que ficou.

E, nesses quase 2 meses,
eu entendi uma coisa que eu não posso negar:

eu quero você na minha vida.

Não só nos momentos bons…
mas em todos.

Mesmo sem saber o que vem pela frente,
mesmo sem ter certeza de nada…
ainda assim, é você que eu escolho.

Porque, de alguma forma,
no meio de tudo que é confuso…
você virou o meu lugar de paz.

Então, antes mesmo do dia 9 chegar…
eu só queria te dizer:

não é só sobre 2 meses.
É sobre você.

E sobre tudo que eu sinto
quando é você. 💜`;

let i = 0;
let tocando = false;

function iniciar() {
  document.getElementById("inicio").style.display = "none";
  document.getElementById("main").style.display = "block";

  const musica = document.getElementById("musica");
  musica.volume = 0.3;
  musica.play().catch(()=>{});
  tocando = true;
  document.getElementById("btnMusica").innerText = "🔊 Música";

  escrever();
  coracoes();
}

function escrever() {
  const el = document.getElementById("texto");

  if (i < mensagem.length) {
    el.innerHTML += mensagem.charAt(i);
    i++;
    setTimeout(escrever, 28);
  }
}

function toggleMusica() {
  const musica = document.getElementById("musica");

  if (tocando) {
    musica.pause();
    document.getElementById("btnMusica").innerText = "🔇 Música";
  } else {
    musica.play();
    document.getElementById("btnMusica").innerText = "🔊 Música";
  }

  tocando = !tocando;
}

function coracoes() {
  setInterval(() => {
    const h = document.createElement("div");
    h.className = "heart";
    h.innerHTML = "💜";
    h.style.left = Math.random() * 100 + "vw";
    document.body.appendChild(h);

    setTimeout(() => h.remove(), 5000);
  }, 300);
}
</script>

</body>
</html>