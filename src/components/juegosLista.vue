<template>
    <div class="listContainer">
        <table>
            <tr>
                <th>Nombre</th>
                <th>Plataforma</th>
                <th>Estado</th>
                <th>Puntaje</th>
                <th>Más info</th>
            </tr>
            <tr v-for="(juego, index) in juegos" :key="index">
                <td>{{ juego.nombre }}</td>
                <td>{{ juego.plataforma }}</td>
                <td>{{ juego.estado }}</td>
                <td>{{ juego.puntaje }}</td>
                <td>
                    <infoButton :juegosInfo="juego" />
                </td>
            </tr>
        </table>
    </div>
</template>

<script setup>
import { defineProps } from "vue"
import infoButton from "./infoButton.vue"
defineProps({
    juegos: Array
})



</script>