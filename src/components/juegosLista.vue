<template>
    <div class="listFilter">
        <h3>Lista de videojuegos</h3>
        <div class="search-container">
            <div class="input-group">
                <label>Nombre: </label>
                <input type="text" id="buscar-nombre">
            </div>

            <div class="input-group">
                <label>Plataforma: </label>
                <select id="buscar-plataforma">
                    <option value="PC">PC</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Playstation">Playstation</option>
                </select>
            </div>

            <div class="input-group">
                <label>Estado: </label>
                <select id="buscar-estado">
                    <option value="Pendiente">Pendiente</option>
                    <option value="Jugando">Jugando</option>
                    <option value="Completado">Completado</option>
                </select>
            </div>
        </div>
    </div>
    <div class="listContainer">
        <!--tabla, conteniendo datos de la lista-->
        <table>
            <tr>
                <th>Nombre</th>
                <th>Plataforma</th>
                <th>Estado</th>
                <th>Puntaje</th>
            </tr>
            <tr v-for="(juego, index) in juegos" :key="index">
                <td>{{ juego.nombre }}</td>
                <td>{{ juego.plataforma }}</td>
                <td>{{ juego.estado }}</td>
                <td>{{ juego.puntaje }}</td>
            </tr>
        </table>
    </div>
</template>

<script setup>
import { defineProps } from "vue"

defineProps({
    juegos: Array
})


</script>