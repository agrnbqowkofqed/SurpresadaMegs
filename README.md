# SurpresadaMegs
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Surpresa de Aniversário</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');
* { box-sizing: border-box; }
body, html {
margin: 0; padding: 0;
font-family: 'Poppins', sans-serif;
height: 100%;
background-color: #ffc0cb;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
color: #4a004a;
text-align: center;
padding: 2rem;
}
.heart-emoji { font-size: 4rem; margin-bottom: 1rem; animation: pulse 2s infinite alternate; }
h1 { font-size: 3rem; font-weight: 700; margin: 0 0 1rem; }
p { font-size: 1.5rem; max-width: 460px; margin: 0 0 2rem; line-height: 1.6; }
button {
font-family: 'Poppins', sans-serif;
font-size: 1.25rem;
padding: 0.75rem 2rem;
background-color: #ff3399;
border: none;
border-radius: 30px;
color: white;
cursor: pointer;
transition: background-color 0.3s ease, transform 0.3s ease;
user-select: none;
margin: 0.5rem;
}
button:hover:not(:disabled) {
background-color: #e62989;
transform: scale(1.1);
}
button:disabled {
background-color: #aaa;
cursor: not-allowed;
transform: none;
}
#question { font-size: 1.75rem; margin-bottom: 1rem; }
#answer-buttons { display: flex; justify-content: center; gap: 1.5rem; margin-bottom: 0.75rem; }
#temp-message {
font-size: 1rem;
color: #660066;
font-style: italic;
height: 1.2em;
margin-bottom: 1.5rem;
opacity: 0;
transition: opacity 0.3s ease;
}
#final-message {
display: none;
margin-top: 2rem;
opacity: 0;
transform: translateY(20px);
animation-fill-mode: forwards;
}
#final-message.show {
display: block;
animation: fadeInUp 1s ease forwards;
}
#final-message img {
max-width: 100%;
height: auto;
border-radius: 15px;
box-shadow: 0 0 10px rgba(255, 51, 153, 0.7);
}
#unlock-control {
font-size: 0.9rem;
color: #88004a;
user-select: none;
}
#unlock-control label { display: block; margin-bottom: 0.3rem; }
#unlock-control input[type="password"] {
padding: 0.4rem 0.8rem;
border: 2px solid #ff3399;
border-radius: 12px;
font-size: 1rem;
width: 130px;
text-align: center;
margin-right: 0.5rem;
transition: border-color 0.3s ease;
}
#unlock-control input[type="password"]:focus {
outline: none;
border-color: #e62989;
}
#unlock-control button {
background-color: #ff3399;
color: white;
border: none;
border-radius: 30px;
padding: 0.5rem 1.2rem;
font-size: 1rem;
cursor: pointer;
transition: background-color 0.3s ease, transform 0.3s ease;
}
#unlock-control button:hover:not(:disabled) {
background-color: #e62989;
transform: scale(1.05);
}
#unlock-control button:disabled { cursor: default; transform: none; }
@keyframes fadeInUp {
from { opacity: 0; transform: translateY(20px); }
to { opacity: 1; transform: translateY(0); }
}
@keyframes pulse {
from { transform: scale(1); opacity: 1; }
to { transform: scale(1.1); opacity: 0.8; }
}
</style>
</head>
<body>

<div class="heart-emoji" aria-label="coração de coração vermelho emoji">❤️</div>
<h1>Heyy Megsss</h1>
<p>hummm tem uma entrega pra vc veyr</p>

<div id="question">Migs, o presente já chegou?</div>
<div id="answer-buttons">
<button id="btnSim" disabled>Sim</button>
<button id="btnAindaNao">Ainda não</button>
</div>

<div id="temp-message" aria-live="polite"></div>

<div id="final-message" aria-live="polite">
<h2>Aproveite Migs! 🎉</h2>
<img src="https://photos.google.com/photo/AF1QipMvL1ApRJUMryz9gL_Dv6wB42qiNsHZoI-y8m8V" alt="Foto surpresa" />
</div>

<div id="unlock-control">
<label for="passwordInput">Digite a senha para liberar "Sim":</label>
<input type="password" id="passwordInput" aria-label="Senha para desbloquear o botão Sim" placeholder="Senha aqui" />
<button id="unlockButton">Desbloquear</button>
<div class="hint">(Use a senha que eu te dei 😊)</div>
</div>

<script>
const btnSim = document.getElementById('btnSim');
const btnAindaNao = document.getElementById('btnAindaNao');
const finalMessage = document.getElementById('final-message');
const question = document.getElementById('question');
const answerButtons = document.getElementById('answer-buttons');
const unlockButton = document.getElementById('unlockButton');
const passwordInput = document.getElementById('passwordInput');
const unlockControl = document.getElementById('unlock-control');
const tempMessage = document.getElementById('temp-message');

const correctPassword = '1505';

btnSim.addEventListener('click', () => {
question.style.display = 'none';
answerButtons.style.display = 'none';
unlockControl.style.display = 'none';
tempMessage.style.opacity = 0;
finalMessage.classList.add('show');
});

btnAindaNao.addEventListener('click', () => {
tempMessage.textContent = 'Calma migs, sem pressa já vai chegar.';
tempMessage.style.opacity = 1;
setTimeout(() => {
tempMessage.style.opacity = 0;
tempMessage.textContent = '';
}, 2000);
});

unlockButton.addEventListener('click', () => {
if (passwordInput.value === correctPassword) {
btnSim.disabled = false;
unlockButton.disabled = true;
passwordInput.disabled = true;
unlockButton.textContent = '"Sim" desbloqueado!';
passwordInput.value = '';
} else {
alert('Senha incorreta, tente novamente!');
passwordInput.value = '';
passwordInput.focus();
}
});
</script>

</body>
</html>
