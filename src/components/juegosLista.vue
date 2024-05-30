<template>
    <div class="listContainer">
        <!--Tabla contenedora de todos los datos, iterandolos-->
        <table id="juegosTable">
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

<style>
#juegosTable{
   margin-left:50ch;
   margin-top: 2.62pc;
}
#juegosTable td, #juegosTable th {
  border: 1px solid #ddd;
  padding: 8px;
}
#juegosTable{
    font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;

    border-collapse: collapse;
    padding: 10px;
}


#juegosTable th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #068f5d;
  color: white;
}
#juegosTable tr:nth-child(even){background-color: #f2f2f2;}

#juegosTable tr:hover {background-color: #ddd;}

</style>

<script setup>
import { defineProps } from "vue"
import infoButton from "./infoButton.vue"
defineProps({
    juegos: Array
})



</script>