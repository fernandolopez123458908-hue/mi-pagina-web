<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gustavo Araca | CV</title>

<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{
    font-family:'Montserrat',sans-serif;
    background:#0f0f0f;
    color:white;
}

/* NAV */
nav{
    display:flex;
    justify-content:center;
    gap:50px;
    padding:25px;
    background:#111;
    font-size:14px;
    letter-spacing:2px;
}
nav a{
    text-decoration:none;
    color:#aaa;
}

/* HERO */
.hero{
    display:flex;
    justify-content:space-between;
    align-items:center;
    padding:60px 10%;
    flex-wrap:wrap;
}

.text{
    max-width:500px;
}

.editable{
    outline:none;
}

h1{
    font-size:48px;
    margin-bottom:20px;
    background:linear-gradient(45deg,#8000ff,#00ffff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
}

.section{
    padding:60px 10%;
    border-top:1px solid #222;
}

.section h2{
    color:#00ffff;
    margin-bottom:20px;
}

img{
    width:350px;
    border-radius:10px;
    box-shadow:0 0 40px rgba(0,255,255,0.3);
}

input[type="file"]{
    margin-top:10px;
    color:white;
}

button{
    margin:20px 10%;
    padding:12px 25px;
    border:none;
    border-radius:10px;
    background:linear-gradient(45deg,#8000ff,#00ffff);
    font-weight:bold;
    cursor:pointer;
}

.robot{
    position:fixed;
    bottom:20px;
    right:20px;
    font-size:40px;
    cursor:pointer;
}
.bubble{
    position:fixed;
    bottom:80px;
    right:20px;
    background:#8000ff;
    padding:10px 15px;
    border-radius:15px;
    display:none;
    font-size:14px;
}
</style>
</head>
<body>

<nav>
<a>BIO</a>
<a>FORMACIÓN</a>
<a>HABILIDADES</a>
<a>CONTACTO</a>
</nav>

<div class="hero">
<div class="text">
<h1 contenteditable="true" class="editable" id="nombre">
Gustavo Alex Araca Chocllo
</h1>

<p contenteditable="true" class="editable" id="descripcion">
Estudiante de Ingeniería de Sistemas apasionado por la tecnología y el desarrollo web.
</p>

<p contenteditable="true" class="editable" id="info">
📍 Sucre, Bolivia <br>
📞 76283322
</p>
</div>

<div>
<img id="foto" src="https://via.placeholder.com/350">
<input type="file" id="subirFoto">
</div>
</div>

<div class="section">
<h2>Formación Académica</h2>
<p contenteditable="true" class="editable" id="formacion">
Bachiller - Marcelo Quiroga Santa Cruz "B"<br>
Ingeniería de Sistemas - Universidad San Francisco Xavier
</p>
</div>

<div class="section">
<h2>Habilidades</h2>
<p contenteditable="true" class="editable" id="habilidades">
Matemáticas · Pensamiento lógico · Desarrollo web
</p>
</div>

<div class="section">
<h2>Idiomas y Motivación</h2>
<p contenteditable="true" class="editable" id="extra">
Español · Quechua · Inglés en desarrollo<br><br>
Elegí esta carrera porque deseo desarrollar soluciones tecnológicas que contribuyan al crecimiento digital.
</p>
</div>

<button onclick="guardar()">Guardar Cambios</button>

<div class="robot" id="robot">🤖</div>
<div class="bubble" id="bubble">Hola Gustavo 🚀</div>

<script>
// Subir foto
document.getElementById("subirFoto").addEventListener("change", function(e){
    const reader = new FileReader();
    reader.onload = function(){
        document.getElementById("foto").src = reader.result;
        localStorage.setItem("foto", reader.result);
    }
    reader.readAsDataURL(e.target.files[0]);
});

// Guardar datos
function guardar(){
    localStorage.setItem("nombre", document.getElementById("nombre").innerHTML);
    localStorage.setItem("descripcion", document.getElementById("descripcion").innerHTML);
    localStorage.setItem("info", document.getElementById("info").innerHTML);
    localStorage.setItem("formacion", document.getElementById("formacion").innerHTML);
    localStorage.setItem("habilidades", document.getElementById("habilidades").innerHTML);
    localStorage.setItem("extra", document.getElementById("extra").innerHTML);
    alert("Cambios guardados correctamente ✔");
}

// Cargar datos guardados
window.onload = function(){
    if(localStorage.getItem("nombre")){
        document.getElementById("nombre").innerHTML = localStorage.getItem("nombre");
        document.getElementById("descripcion").innerHTML = localStorage.getItem("descripcion");
        document.getElementById("info").innerHTML = localStorage.getItem("info");
        document.getElementById("formacion").innerHTML = localStorage.getItem("formacion");
        document.getElementById("habilidades").innerHTML = localStorage.getItem("habilidades");
        document.getElementById("extra").innerHTML = localStorage.getItem("extra");
        document.getElementById("foto").src = localStorage.getItem("foto");
    }
};

// Robot
document.getElementById("robot").addEventListener("click",()=>{
let bubble=document.getElementById("bubble");
bubble.style.display="block";
setTimeout(()=>bubble.style.display="none",3000);
});
</script>

</body>
</html>
