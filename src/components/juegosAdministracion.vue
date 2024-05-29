<template>
    <div class="appContainer">
        <h1>Administración de videojuegos</h1>
        <div class="form-container">
            <h2>Nuevo videojuego</h2>
            <div class="input-group">
                <label>Nombre: </label>
                <input type="text" v-model="juegosDatos.nombre">

                <label>Plataforma: </label>
                <select id="plataforma" v-model="juegosDatos.plataforma">
                    <option value="PC">PC</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Playstation">Playstation</option>
                </select><br>

                <label>Estado: </label>
                <select id="estado" v-model="juegosDatos.estado">
                    <option value="Pendiente">Pendiente</option>
                    <option value="Jugando">Jugando</option>
                    <option value="Completado">Completado</option>
                </select>
            </div>

            <label>Puntaje: </label>
            <input type="number" v-model="juegosDatos.puntaje" min=1 max=10>
        </div>
        <button @click="handleSend">Registrar videojuego</button>
    </div>
    <listContainer :juegos="juegos" />
    <modalError v-if="showModalError" :razon="razon" :contenido="contenido" @close="closeModalError"/>
</template>

<script setup>
import listContainer from "./juegosLista.vue"
import modalError from "./modalError.vue"
import { ref } from "vue"
// Objecto que contiene los datos bindeados a los input
const juegosDatos = ref({
    nombre: "",
    plataforma: "PC",
    estado: "Pendiente",
    puntaje: 1
})
let showModalError = ref(false)
let razon, contenido = ""
// Array que contendrá los datos de juegosDatos
let juegos = ref([])
// Verificacion de errores
function errores(puntaje, nombre) {
    if (puntaje < 1 || puntaje > 10) {
        razon = "Ingrese un puntaje válido."
        contenido = "El puntaje debe ser un número mayor a 0 y menor a 10"
        showModalError.value = true
        return true
    }
    if (nombre == "") {
        razon = "Ingrese un nombre válido."
        contenido = "El nombre no puede estar vacío."
        showModalError.value = true
        return true
    }
    return false
}
// Luego de agregar los datos al array, esta función limpiará los input
function limpiarInput() {
    juegosDatos.value = {
        nombre: "",
        plataforma: "PC",
        estado: "Pendiente",
        puntaje: 1
    }
}
// Agrega, en caso de no encontrar errores, los datos al array "juegos"
const handleSend = () => {
    if (!(errores(juegosDatos.value.puntaje, juegosDatos.value.nombre))) {
        juegos.value.push({
            nombre: juegosDatos.value.nombre,
            plataforma: juegosDatos.value.plataforma,
            estado: juegosDatos.value.estado,
            puntaje: juegosDatos.value.puntaje,
        })
    }
    limpiarInput()
}

function closeModalError() {
    showModalError.value = false
}

</script>

<style scoped>
select,
button {
    cursor: pointer;
}
</style>