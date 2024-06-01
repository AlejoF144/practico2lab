<template>
    <div class="appContainer">
        <div id="tittle">
            <h1>Administración de videojuegos</h1>
        </div>
        <div></div>
        <div class="form-container">
            <h2>Nuevo videojuego</h2>
            <div class="input-group">
                <label>Nombre: </label>
                <input type="text" v-model="juegosDatos.nombre">
                <div class="nombreError" v-if="juegosDatos.nombre == ''">Nombre no valido.</div>

                <label>Plataforma: </label>
                <select id="plataforma" v-model="juegosDatos.plataforma">
                    <option value="" disabled selected>PC | PlayStation | Xbox One</option>
                    <option value="PC">PC</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Playstation">Playstation</option>
                </select><br>

                <label>Estado: </label>
                <select id="estado" v-model="juegosDatos.estado">
                    <option value="" disabled selected>Pendiente | Jugando | Completado</option>
                    <option value="Pendiente">Pendiente</option>
                    <option value="Jugando">Jugando</option>
                    <option value="Completado">Completado</option>
                </select>
            </div>

            <label>Puntaje: </label>
            <input type="number" v-model="juegosDatos.puntaje" min=1 max=10>
            <div class="puntajeError" v-if="juegosDatos.puntaje < 1 || juegosDatos.puntaje > 10">Puntaje no valido.</div>
            <button id="btnRegistrar" @click="handleSend">Registrar videojuego</button>
        </div>

    </div>
    <!--Componente que recibe el array contenedor de todos los juegos-->
    <listContainer :juegos="juegos" />
</template>

<script setup>
import listContainer from "./juegosLista.vue"
import { ref } from "vue"
// Objecto que contiene los datos bindeados a los input
const juegosDatos = ref({
    nombre: "",
    plataforma: "",
    estado: "",
    puntaje: 1
})
// Array que contendrá los datos de juegosDatos
let juegos = ref([])

// Luego de agregar los datos al array, esta función limpiará los input
function limpiarInput() {
    juegosDatos.value = {
        nombre: "",
        plataforma: "",
        estado: "",
        puntaje: 1
    }
}
// Verificacion de errores
function errores(puntaje, nombre, estado, plataforma) {
    if (puntaje < 1 || puntaje > 10) {
        return true
    }
    if (nombre == "" || estado == "" || plataforma == "") {
        return true
    }
    return false
}
// Agrega, en caso de no encontrar errores, los datos al array "juegos"
const handleSend = () => {
    if (!errores(juegosDatos.value.puntaje, juegosDatos.value.nombre, juegosDatos.value.estado, juegosDatos.value.plataforma)) {
        juegos.value.push({
            nombre: juegosDatos.value.nombre,
            plataforma: juegosDatos.value.plataforma,
            estado: juegosDatos.value.estado,
            puntaje: juegosDatos.value.puntaje,
        })
    }
    limpiarInput()
}

</script>

<style scoped >
#tittle {
    text-align: center;
}

.form-container {
    width: 400px;
    /* Ancho del rectángulo */
    min-height: 300px;
    /* Altura mínima del rectángulo */
    border: 1px solid #ccc;
    /* Borde del rectángulo */
    border-radius: 4px;
    /* Bordes ligeramente redondeados */
    padding: 20px;
    /* Espaciado interno */
    margin: 20px 0;
    /* Espaciado superior e inferior */
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    /* Sombra para darle profundidad */
    background-color: #f9f9f9;
    /* Color de fondo */
    float: left;
    /* Alinear a la izquierda */
}


h1,
h2 {
    color: #333;
}

.input-group,
table {
    width: 100%;
    margin-top: 20px;
}


input[type="text"],
select,
input[type="number"] {
    width: 100%;
    padding: 8px;
    margin: 5px 0;
    box-sizing: border-box;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    background-color: #068f5d;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    background-color: #046b4a;
}

/* Error messages styling */
.nombreError,
.puntajeError {
    color: #d9534f;
    font-size: 14px;
}
</style>