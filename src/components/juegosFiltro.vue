<template>
    <div class="listFilter">
        <h2>Busqueda de videojuegos</h2>
        <div class="search-container">
            <div class="input-group">
                <label>Nombre: </label><br>
                <input type="text" class="buscarNombre" @input="search"><br>

                <label>Plataforma: </label><br>
                <select class="buscarPlataforma" @input="search">
                    <option value="" disabled selected>PC | PlayStation | Xbox One</option>
                    <option value="PC">PC</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Playstation">Playstation</option>
                </select><br>

                <label>Estado: </label><br>
                <select class="buscarEstado" @input="search">
                    <option value="" disabled selected>Pendiente | Jugando | Completado</option>
                    <option value="Pendiente">Pendiente</option>
                    <option value="Jugando">Jugando</option>
                    <option value="Completado">Completado</option>
                </select>
            </div>
        </div>
    </div>
</template>

<script setup>
import { defineEmits } from "vue"
const emit = defineEmits(["search"])

const search = (e) => {
    emit("search", e.target.value)
}

</script>

<style scoped>
#tittle {
    text-align: center;
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
</style>