<template>
    <div class="infoButton">
        <button @click="toggleModal">info</button>
    </div>
    <!--modal es el componente a mostrar en caso de que el botón sea presionado-->
    <modal v-if="showModal" @close="toggleModal()" :juegosInfo="juegosInfo" />
</template>

<script setup>
import { defineProps, ref } from "vue"
import modal from "./modalMasInfo.vue"
defineProps({
    juegosInfo: Array
})
// Mostrará el modal con la información en caso de que se aprete el botón
let showModal = ref(false)
const toggleModal = () => { 
    showModal.value = !showModal.value 
}

</script>

<style scoped></style>