<template>
    <div class="listContainer">
    <div class="filtrado">
        <listFilter @search="handleSearch" />
        <button @click="clearSearch">Lista Completa</button>
    </div>
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
.filtrado {
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
    float: left;
    /* Alinear a la izquierda */
    background-color: rgb(1, 223, 116);
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
#juegosTable {
  width: 100%; /* Hace que la tabla use todo el ancho disponible */
  table-layout: auto; /* Permite que la tabla ajuste el ancho de las columnas automáticamente */
  border-collapse: collapse; /* Opcional: para estilos de borde */
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
    background-color: rgb(1, 223, 116);
}

#juegosTable tr:hover {
    background-color: #ddd;
}
</style>

