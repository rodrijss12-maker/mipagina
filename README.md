<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>San Valentín 💜</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&family=Pacifico&display=swap" rel="stylesheet">

<style>
body {
    font-family: 'Roboto', sans-serif;
    background: linear-gradient(135deg,#f3e8ff,#e0aaff,#ffccd5);
    background-size: 400% 400%;
    animation: gradientMove 10s ease infinite;
    color: #4b006e;
    margin: 0;
    padding: 0;
    text-align: center;
    overflow-x: hidden;
}

@keyframes gradientMove {
    0% {background-position: 0% 50%;}
    50% {background-position: 100% 50%;}
    100% {background-position: 0% 50%;}
}

canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
}

.container {
    padding: 20px;
}

h1 {
    font-family: 'Pacifico', cursive;
    color: #9d4edd;
    font-size: 3em;
    margin-bottom: 20px;
    animation: fadeIn 2s, pulse 2s infinite;
}

@keyframes pulse {
    0% {transform: scale(1);}
    50% {transform: scale(1.08);}
    100% {transform: scale(1);}
}

.image-container {
    margin-top: 20px;
}

img {
    width: 80%;
    max-width: 500px;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(157,78,221,0.5);
    transition: 0.5s;
}
img:hover {
    transform: scale(1.05);
}

.message {
    margin-top: 20px;
    font-size: 1.2em;
    font-weight: bold;
}

.content-section {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    margin: 30px;
}

.reasons {
    width: 100%;
    max-width: 500px;
    text-align: left;
    margin-bottom: 30px;
}

.reasons ul {
    list-style: none;
    padding-left: 0;
}

.reasons li {
    font-size: 1.2em;
    margin: 10px 0;
    color: #7b2cbf;
}

.video-container {
    width: 100%;
    max-width: 600px;
    margin-bottom: 50px;
}

iframe {
    width: 100%;
    height: 400px;
    border-radius: 15px;
    box-shadow: 0 8px 20px rgba(157,78,221,0.4);
}

.footer {
    background: linear-gradient(90deg,#9d4edd,#ff4d6d);
    color: white;
    padding: 15px;
    margin-top: 30px;
}

.button-container {
    margin-top: 20px;
}

.love-button {
    background: linear-gradient(45deg,#c77dff,#ff4d6d);
    color: white;
    font-size: 1.2em;
    padding: 12px 25px;
    border: none;
    border-radius: 30px;
    cursor: pointer;
    box-shadow: 0 0 15px rgba(199,125,255,0.7);
    transition: 0.4s;
}

.love-button:hover {
    transform: scale(1.1);
    box-shadow: 0 0 25px rgba(255,77,109,0.9);
}

.hidden-message {
    margin-top: 15px;
    font-size: 1.4em;
    font-weight: bold;
    display: none;
}

@keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
}

@media (max-width: 768px) {
    .content-section {
        flex-direction: column;
        align-items: center;
    }
    .reasons, .video-container {
        width: 90%;
    }
}
</style>
</head>

<body>

<canvas id="heartCanvas"></canvas>

<div class="container">
<h1>¡Feliz Día de San Valentín! 💜</h1>

<div class="image-container">
<img src="img/collage.jfif" alt="Imagen de San Valentín">
</div>

<div class="message">
<p>
Hoy es el Día de San Valentín. Desde que te conozco, todo tiene un brillo diferente. El cariño que tengo por ti es más grande de lo que podría decir. Cada vez que miro tus ojos, veo un futuro lleno de momentos hermosos, de risas y de sueños compartidos. Te quiero con todo mi ser y me siento afortunado de tenerte en mi vida. ¡Feliz Día de San Valentín! 💖
</p>
<p>¡Te quiero demasiadooooo mi linda mujer!</p>
</div>
</div>

<section class="content-section">

<div class="reasons">
<b>Razones por las que te amo:</b>
<ul>
<li>1. Eres hermosa</li>
<li>2. Eres todo para mí</li>
<li>3. Porque sí 💕</li>
<li>4. Me tratas de una manera única</li>
<li>5. Eres especial</li>
<li>6. Alegras mis días</li>
<li>7. Tu sonrisa ilumina mi mundo</li>
<li>8. Porque mi corazón te eligió 💜</li>
</ul>
</div>

<div class="video-container">
<h2>Te dedico esta canción 🎵</h2>
<iframe src="https://www.youtube.com/embed/gZTYjF2Vvpc?si=dkxWbV24LmqrwaED" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

<div class="button-container">
<button onclick="showLoveMessage()" class="love-button">
Haz clic para ver mi amor crecer ❤️
</button>
<p id="love-message" class="hidden-message"></p>
</div>

</section>

<div class="footer">
<b>CREADO CON MUCHO 💜 PARA TI</b>
</div>

<script>
const canvas = document.getElementById('heartCanvas');
const ctx = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let hearts = [];
const colors = ["#ff4d6d","#ff8fab","#c77dff","#9d4edd","#e0aaff"];

function createHeart(xPos=null,yPos=null){
    hearts.push({
        x: xPos || Math.random()*canvas.width,
        y: yPos || canvas.height+20,
        size: Math.random()*18+10,
        color: colors[Math.floor(Math.random()*colors.length)],
        speed: Math.random()*2+1,
        opacity: Math.random()*0.8+0.2
    });
}

function drawHeart(x,y,size,color,opacity){
    ctx.save();
    ctx.globalAlpha = opacity;
    ctx.fillStyle = color;
    ctx.beginPath();
    ctx.moveTo(x,y);
    ctx.bezierCurveTo(x-size/2,y-size/2,x-size,y+size/3,x,y+size);
    ctx.bezierCurveTo(x+size,y+size/3,x+size/2,y-size/2,x,y);
    ctx.fill();
    ctx.restore();
}

function updateHearts(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    for(let i=0;i<hearts.length;i++){
        hearts[i].y -= hearts[i].speed;
        hearts[i].x += Math.sin(hearts[i].y*0.03);
        if(hearts[i].y < -20){
            hearts.splice(i,1);
            i--;
        } else {
            drawHeart(hearts[i].x,hearts[i].y,hearts[i].size,hearts[i].color,hearts[i].opacity);
        }
    }
}

function animate(){
    updateHearts();
    requestAnimationFrame(animate);
}

/* Lluvia automática */
setInterval(()=>createHeart(), 120);

/* Explosión al cargar */
window.onload = function(){
    for(let i=0;i<60;i++){
        createHeart(canvas.width/2, canvas.height/2);
    }
}

animate();

function showLoveMessage(){
    const message = document.getElementById('love-message');
    message.textContent = "💜 Mi amor por ti es infinito y cada día crece más 💞";
    message.style.display = 'block';
}
</script>

</body>
</html>
