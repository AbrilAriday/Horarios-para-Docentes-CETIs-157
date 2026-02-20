<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Horario Escolar - Profesores</title>

<style>
/* ------------------------------
   ESTILO GLOBAL ELEGANTE
------------------------------ */
body {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    padding: 35px;
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #fff;
    position: relative;
    overflow-x: hidden;
}

body::before {
    content: "";
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;

    background:
        linear-gradient(rgba(0,0,0,0.65), rgba(0,0,0,0.65)),
        url("https://www.colimanoticias.com/wp-content/uploads/2020/12/CETIs-157-768x480.png?v=1608170964");

    background-size: cover;
    background-position: center;
    z-index: -1;
}


/* ------- Animaciones generales ------- */
@keyframes fadeSlide {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes highlightAppear {
    0%   { transform: scale(0.90); box-shadow: 0 0 0px rgba(255,255,255,0); opacity: 0; }
    40%  { transform: scale(1.05); box-shadow: 0 0 25px rgba(255,255,255,0.65); opacity: 1; }
    70%  { transform: scale(0.98); box-shadow: 0 0 14px rgba(255,255,255,0.4); }
    100% { transform: scale(1); box-shadow: 0 0 0px rgba(255,255,255,0); }
}

.resaltado {
    animation: highlightAppear 1s ease !important;
}

/* ------------------------------
   TITULOS
------------------------------ */
h1, h2 {
    text-align: center;
    font-weight: 700;
    letter-spacing: 1px;
    margin-bottom: 20px;
    animation: fadeSlide .6s ease both;
}

/* ------------------------------
   GLASS PANEL RECONFIGURADO
------------------------------ */
.glass {
    width: 70%;                 /* ancho del panel */
    padding: 20px;              /* espacio interno */
    backdrop-filter: blur(20px);
    background: rgba(255, 255, 255, 0.12);
    border-radius: 20px;
    margin-bottom: 40px;
    border: 1px solid rgba(255,255,255,0.2);
    box-shadow: 0px 12px 35px rgba(0,0,0,0.35);
    animation: fadeSlide .7s ease;
    transition: transform .25s ease;
}

/* efecto hover para levantar el panel */
.glass:hover {
    transform: translateY(-4px);
}

/* contenedor de horarios personales centrado */
#contenedor-horarios {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center; /* centra los paneles hijos */
}

/* contenedor de botones centrado */
.btns-bottom {
    width: 100%;
    display: flex;
    justify-content: center;
    margin-top: 20px; /* separación del contenido */
}

/* contenedor de botones dentro del horario general */
.glass .btns {
    width: 100%;
    display: flex;
    justify-content: center;
    gap: 10px; /* espacio entre botones */
    margin-bottom: 20px;
}


.glass:hover {
    transform: translateY(-4px);
}

/* ------------------------------
   BUSCADOR ELEGANTE
------------------------------ */
#buscador-profesores {
    width: 60%;
    padding: 14px;
    font-size: 17px;
    border-radius: 12px;
    border: none;
    outline: none;
    text-align: center;
    background: rgba(255,255,255,0.18);
    backdrop-filter: blur(8px);
    color: #fff !important;
    transition: .25s;
    box-shadow: 0 4px 18px rgba(0,0,0,0.3);
    margin-bottom: 25px;
}

#buscador-profesores::placeholder {
    color: #f5f5f5 !important;
}

#buscador-profesores:focus {
    box-shadow: 0 0 15px #8fd3f4;
    background: rgba(255,255,255,0.25);
}

/* ------------------------------
   BOTONES ELEGANTES
------------------------------ */
button {
    padding: 10px 18px;
    border-radius: 10px;
    border: none;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    color: #fff;
    background: linear-gradient(135deg, #74ebd5, #ACB6E5);
    transition: .25s;
    box-shadow: 0 3px 14px rgba(0,0,0,0.35);
}

button:hover {
    transform: translateY(-3px);
    box-shadow: 0 5px 20px rgba(255,255,255,0.4);
}

button.eliminar {
    background: #cc0033;
}
button.eliminar:hover {
    background: #ff0033;
}

/* ------------------------------
   TABLAS
------------------------------ */
table {
    width: 100%;
    border-collapse: collapse;
    overflow: hidden;
    border-radius: 16px;
    margin-top: 10px;
    animation: fadeSlide .8s;
}

thead {
    background: rgba(255,255,255,0.18);
    backdrop-filter: blur(12px);
}

th, td {
    padding: 8px;
}

td {
    background: rgba(255,255,255,0.10);
    border-bottom: 1px solid rgba(255,255,255,0.12);
    transition: background .2s;
}

tr:hover td {
    background: rgba(255, 255, 255, 0.2);
}

/* ------------------------------
   INPUTS Y SELECTS
------------------------------ */
input, select {
    width: 95%;
    padding: 6px;
    border-radius: 8px;
    border: 1px solid rgba(255, 255, 255, 0.25);
    background: rgba(0, 0, 0, 0.18);
    color: #fff;
    outline: none;
    transition: .25s;
    margin-bottom: 4px;
}

input:focus, select:focus {
    box-shadow: 0 0 10px #8ed6ff;
    background: rgba(255,255,255,0.25);
}

select option { color: #000; }

@media print {

    /* Ocultar todo */
    body * {
        visibility: hidden;
    }

    /* Mostrar solo el contenedor principal */
    #glass-general,
    #glass-general * {
        visibility: visible;
    }

    /* Ocultar los botones del horario */
    #glass-general .btns {
        display: none;
    }

    /* Ajustes para que quepa en una sola hoja Letter horizontal */
    #glass-general {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        padding: 5px;
        font-size: 11px;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        page-break-inside: avoid;
    }

    th, td {
        padding: 3px 5px;
    }

    body {
        background: #fff;
        color: #000;
    }

    @page {
        size: letter landscape;
        margin: 10mm;
    }
}

#logo {
    width: 140px;      /* Ajusta el tamaño si quieres */
    margin-bottom: 15px;
    display: block;
}

</style>
</head>

<body>

<h1>Horario Escolar - Profesores</h1>

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgscrENWH7psY4rA2Xy6AWwpqJ2X-AGEBu4fVL5vKBHDY1Z-tCqsk-cHUe3qQ2iRICCNFX64htTMt7KQcSgc357byhgHxm3CvNx5jcHlxwXC987SjR1r6rU24CoMKEqlR3zK7NmuF8OcBQ1/s2048/Imagotipo_DGETI.png" alt="Logo DGETI" id="logo" />


<div class="glass" id="glass-general">
    <div class="btns">
        <button disabled>Guardado automático</button>
        <button onclick="borrarHorarioGeneral()">Borrar todo</button>
        <button onclick="window.print()">Exportar PDF</button>
    </div>

    <table>
        <thead>
            <tr>
                <th>Hora</th>
                <th>Lunes</th>
                <th>Martes</th>
                <th>Miércoles</th>
                <th>Jueves</th>
                <th>Viernes</th>
            </tr>
        </thead>
        <tbody id="tabla-horarios"></tbody>
    </table>
</div>

<input type="text" id="buscador-profesores" placeholder="Buscar profesor..." oninput="filtrarHorarios()">

<h2>Horarios personales de profesores</h2>
<div id="contenedor-horarios"></div>

<div class="btns-bottom">
    <button onclick="crearNuevoHorarioPersonal()">➕ Agregar horario personal</button>
</div>

<script>/* DATOS BASE */
const horas = [
    "7:00 - 7:50","7:50 - 8:40","8:40 - 9:30","9:30 - 10:00 (Receso)",
    "10:00 - 10:50","10:50 - 11:40","11:40 - 12:30","12:30 - 13:20","13:20 - 14:10"
];

const salones = [
    "A-1","A-2","A-3","A-4","A-5","A-6","A-7","A-8","A-9","A-10",
    "A-11","A-12","A-13","A-14","Centro de Cómputo 1","Centro de Cómputo 2",
    "Laboratorio de Usos Múltiples","Laboratorio de Análisis","Sala Audio Visual"
];

const grupos = [];
for (let g = 1; g <= 6; g++) ["A","B","C","D"].forEach(s => grupos.push(`${g}-${s}`));

/* ---------------------------------
   VALIDAR CONFLICTO DE SALONES (solo personal)
----------------------------------*/
function validarConflictoSalonPersonal(origenKey, salonSeleccionado) {
    if (!salonSeleccionado) return false;

    // Solo aplicamos si el select pertenece a un horario personal
    if (!origenKey.startsWith("personal")) return false;

    const partes = origenKey.split("-");
    const horaIndex = partes[2];
    const diaIndex  = partes[3];

    let conflicto = false;

    // Recorre solo selects de horarios personales
    document.querySelectorAll("select[data-key^='personal']").forEach(sel => {
        if (sel.dataset.key === origenKey) return; // ignora el propio select

        const p = sel.dataset.key.split("-");
        const h = p[2];
        const d = p[3];

        if (h == horaIndex && d == diaIndex && sel.value === salonSeleccionado) {
            conflicto = true;
        }
    });

    return conflicto;
}

/* ---------------------------------
   HORARIO GENERAL
----------------------------------*/
function crearHorarioGeneral() {
    const tabla = document.getElementById("tabla-horarios");
    tabla.innerHTML = "";

    horas.forEach((hora, i) => {
        let tr = document.createElement("tr");

        let th = document.createElement("td");
        th.innerText = hora;
        tr.appendChild(th);

        for (let d = 0; d < 5; d++) {

            let td = document.createElement("td");

            if (hora.includes("Receso")) {
                td.innerHTML = "<b>---</b>";
            } else {

                let selSalon = document.createElement("select");
                selSalon.innerHTML =
                    `<option value="">Salón...</option>` +
                    salones.map(s=>`<option value="${s}">${s}</option>`).join("");

                let inputMateria = document.createElement("input");
                inputMateria.placeholder = "Materia";

                let inputMaestro = document.createElement("input");
                inputMaestro.placeholder = "Maestro / Grupo";

                selSalon.onchange = function() {
                    cargarDatosSalon(i, d, selSalon.value, inputMateria, inputMaestro);
                };

                inputMateria.oninput = function() {
                    guardarDatosSalon(i, d, selSalon.value, inputMateria.value, inputMaestro.value);
                };

                inputMaestro.oninput = function() {
                    guardarDatosSalon(i, d, selSalon.value, inputMateria.value, inputMaestro.value);
                };

                td.appendChild(selSalon);
                td.appendChild(inputMateria);
                td.appendChild(inputMaestro);
            }

            tr.appendChild(td);
        }

        tabla.appendChild(tr);
    });
}


function guardarDatosSalon(horaIndex, diaIndex, salon, materia, maestro) {

    if (!salon) return;

    const key = `general-${horaIndex}-${diaIndex}-${salon}`;

    const datos = {
        materia: materia,
        maestro: maestro
    };

    localStorage.setItem(key, JSON.stringify(datos));
}


function cargarDatosSalon(horaIndex, diaIndex, salon, inputMateria, inputMaestro) {

    inputMateria.value = "";
    inputMaestro.value = "";

    if (!salon) return;

    const key = `general-${horaIndex}-${diaIndex}-${salon}`;
    const datos = JSON.parse(localStorage.getItem(key));

    if (datos) {
        inputMateria.value = datos.materia || "";
        inputMaestro.value = datos.maestro || "";
    }
}


function borrarHorarioGeneral() {
    if(confirm("¿Seguro que deseas borrar todo el horario general?")){
        Object.keys(localStorage).forEach(k=>{
            if(k.startsWith("general-"))
                localStorage.removeItem(k);
        });
        location.reload();
    }
}


/* ---------------------------------
   HORARIOS PERSONALES
----------------------------------*/
function getListaHorarios(){ 
    return JSON.parse(localStorage.getItem("listaHorariosPersonales")||"[]"); 
}

function guardarListaHorarios(lista){ 
    localStorage.setItem("listaHorariosPersonales", JSON.stringify(lista)); 
}

function crearNuevoHorarioPersonal(id=Date.now()){
    const cont=document.getElementById("contenedor-horarios");
    let lista=getListaHorarios();
    if(!lista.includes(id)){ lista.push(id); guardarListaHorarios(lista); }

    const div=document.createElement("div");
    div.classList.add("glass"); 
    div.id=`personal-${id}`;
    div.innerHTML=`
        <h2>Horario personal</h2>
        <label>Nombre del profesor:</label>
        <input id="prof-${id}" placeholder="Nombre del profesor" style="margin-bottom:15px;">
        <button class="eliminar" onclick="eliminarHorarioPersonal(${id})">
        ❌ Eliminar este horario</button>
        <table>
            <thead>
                <tr>
                    <th>Hora</th>
                    <th>Lunes</th><th>Martes</th><th>Miércoles</th>
                    <th>Jueves</th><th>Viernes</th>
                </tr>
            </thead>
            <tbody id="tabla-${id}"></tbody>
        </table>`;
    cont.appendChild(div);
    generarTablaPersonal(id);
}

function generarTablaPersonal(id){
    const tbody=document.getElementById(`tabla-${id}`);
    horas.forEach((hora,h)=>{
        let tr=document.createElement("tr");
        let th=document.createElement("td"); 
        th.innerText=hora; 
        tr.appendChild(th);

        for(let d=0;d<5;d++){
            let td=document.createElement("td");

            if(hora.includes("Receso")) td.innerHTML="<b>---</b>";
            else{
                const selSalon=document.createElement("select");
                selSalon.dataset.key=`personal-${id}-${h}-${d}-salon`;
                selSalon.innerHTML=`<option value="">Salón...</option>`+
                    salones.map(s=>`<option>${s}</option>`).join("");

                const inputMateria=document.createElement("input");
                inputMateria.dataset.key=`personal-${id}-${h}-${d}-materia`;
                inputMateria.placeholder="Materia";

                const inputMaestro=document.createElement("input");
                inputMaestro.dataset.key=`personal-${id}-${h}-${d}-maestro`;
                inputMaestro.placeholder="Grado y Grupo";

                selSalon.value=localStorage.getItem(selSalon.dataset.key)||"";
                inputMateria.value=localStorage.getItem(inputMateria.dataset.key)||"";
                inputMaestro.value=localStorage.getItem(inputMaestro.dataset.key)||"";

                // 🚀 Aquí usamos la validación SOLO para personales
                selSalon.onchange = function() {
                    if (validarConflictoSalonPersonal(this.dataset.key, this.value)) {
                        alert("⚠️ Este salón ya está ocupado en ese día y hora.");
                        this.value = "";
                        return;
                    }
                    guardarHorariosPersonales();
                };
                inputMateria.oninput=guardarHorariosPersonales;
                inputMaestro.oninput=guardarHorariosPersonales;

                td.appendChild(selSalon);
                td.appendChild(inputMateria);
                td.appendChild(inputMaestro);
            }
            tr.appendChild(td);
        }
        tbody.appendChild(tr);
    });

    const nombreProf=document.getElementById(`prof-${id}`);
    nombreProf.value=localStorage.getItem(`prof-${id}`)||"";
    nombreProf.oninput=guardarHorariosPersonales;
}

function guardarHorariosPersonales(){
    document.querySelectorAll("[data-key]").forEach(el=>{
        if(el.dataset.key.includes("personal"))
            localStorage.setItem(el.dataset.key,el.value);
    });
    document.querySelectorAll("[id^='prof-']").forEach(el=>
        localStorage.setItem(el.id,el.value)
    );
}

function eliminarHorarioPersonal(id){
    if(confirm("¿Eliminar este horario personal?")){
        Object.keys(localStorage).forEach(k=>{
            if(k.includes(`personal-${id}`)||k===`prof-${id}`)
                localStorage.removeItem(k);
        });
        let lista=getListaHorarios().filter(x=>x!==id);
        guardarListaHorarios(lista);
        document.getElementById(`personal-${id}`).remove();
    }
}

/* ---------------------------------
   BUSCADOR
----------------------------------*/
function filtrarHorarios(){
    const texto=document.getElementById("buscador-profesores").value.toLowerCase();
    const cont=document.getElementById("contenedor-horarios");
    Array.from(cont.children).forEach(div=>{
        const nombre=(div.querySelector("input[id^='prof-']").value||"").toLowerCase();
        div.style.display=(texto===""||nombre.includes(texto))?"block":"none";
    });
}

/* ---------------------------------
   INICIALIZAR
----------------------------------*/
crearHorarioGeneral();
getListaHorarios().forEach(id=>crearNuevoHorarioPersonal(id));

/* ---------------------------------
   TECLA ENTER: mover al siguiente input en la misma celda
----------------------------------*/
function habilitarEnterParaInputs() {
    document.querySelectorAll("td input").forEach(input => {
        input.addEventListener("keydown", function(e) {
            if (e.key === "Enter") {
                e.preventDefault(); // evitar que haga submit

                // Encuentra todos los inputs en la misma celda
                const inputs = Array.from(this.parentElement.querySelectorAll("input"));
                const index = inputs.indexOf(this);

                // Si hay un siguiente input, fócalo
                if (index >= 0 && index < inputs.length - 1) {
                    inputs[index + 1].focus();
                } 
                // Si es el último, no hace nada
            }
        });
    });
}

// Llamar a la función después de crear todos los horarios
habilitarEnterParaInputs();

</script>

</body>
</html>
