<template>
    <div class="listContainer">
        <listFilter @search="handleSearch" />
        <button @click="clearSearch">Clear Search</button>

        <!--Tabla contenedora de todos los datos, iterandolos-->
        <table id="juegosTable">
            <tr>
                <th>Nombre</th>
                <th>Plataforma</th>
                <th>Estado</th>
                <th>Puntaje</th>
                <th>Más info</th>
            </tr>
            <tr v-for="(juego, index) in filteredItems" :key="index">
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
import { defineProps, computed, ref } from "vue"
import infoButton from "./infoButton.vue"
import listFilter from "./juegosFiltro.vue"

const props = defineProps({
    juegos: Array
})

const searchFilter = ref('')

const filteredItems = computed(() => {
    if (searchFilter.value != "") {
        return props.juegos.filter(item =>
            item.nombre.includes(searchFilter.value) ||
            item.estado.includes(searchFilter.value) ||
            item.plataforma.includes(searchFilter.value))
    }
    return props.juegos
})

const handleSearch = (search) => {
    searchFilter.value = search
}
const clearSearch = () => {
    searchFilter.value = ""
}
</script>
<style scoped>
#juegosTable {
    margin-left: 60ch;
    margin-top: 2.62pc;
}

#juegosTable td,
#juegosTable th {
    border: 1px solid #ddd;
    padding: 8px;
}

#juegosTable {
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

#juegosTable tr:nth-child(even) {
    background-color: #f2f2f2;
}

#juegosTable tr:hover {
    background-color: #ddd;
}
</style>

