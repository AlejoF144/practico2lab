<template>
    <div class="appContainer">
        <h1>Administración de videojuegos</h1>
        <div class="form-container">
            <h2>Nuevo videojuego</h2>
            <label>Nombre: </label>
            <input type="text" v-model="juegosDatos.nombre">


            <div class="input-group">
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
</template>

<script setup>
import listContainer from "./juegosLista.vue"
import { ref } from "vue"

const juegosDatos = ref({
    nombre: "",
    plataforma: "PC",
    estado: "Pendiente",
    puntaje: 1
})
let juegos = ref([])
function errores(puntaje, nombre) {
    // Verificacion de errores
    if (puntaje < 1 || puntaje > 10) {
        return true
    }
    if (nombre == "") {
        return true
    }
    return false
}
function limpiarInput() {
    juegosDatos.value = {
        nombre: "",
        plataforma: "PC",
        estado: "Pendiente",
        puntaje: 1
    }
}
const handleSend = () => {
    if (errores(juegosDatos.value.puntaje, juegosDatos.value.nombre)) {
        alert(":(")
    } else {
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

<style scoped>
select,
button {
    cursor: pointer;
}
</style>