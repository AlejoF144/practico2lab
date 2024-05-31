<template>
    <div class="listFilter">
        <h3>Lista de videojuegos</h3>
        <div class="search-container">
            <div class="input-group">
                <label>Nombre: </label>
                <input type="text" class="buscarNombre" @input="search">

                <label>Plataforma: </label>
                <select class="buscarPlataforma" @input="search">
                    <option value="PC">PC</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Playstation">Playstation</option>
                </select>

                <label>Estado: </label>
                <select class="buscarEstado" @input="search">
                    <option value="Pendiente">Pendiente</option>
                    <option value="Jugando">Jugando</option>
                    <option value="Completado">Completado</option>
                </select>
            </div>
        </div>
    </div>
</template>

<script setup>
import { defineEmits} from "vue"
const emit = defineEmits(["search"])

const search = (e) => {
    emit("search", e.target.value)   
}

</script>

<style scoped></style>