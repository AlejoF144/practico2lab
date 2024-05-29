<template>
    <div class="infoButton">
        <button @click="toggleModal">+</button>
    </div>
    <modal v-if="showModal" @close="toggleModal()" :juegosInfo="juegosInfo" />
</template>

<script setup>
import { defineProps, ref } from "vue"

import modal from "./modalMasInfo.vue"
defineProps({
    juegosInfo: Array
})
let showModal = ref(false)
const toggleModal = () => { 
    showModal.value = !showModal.value 
}

</script>

<style scoped></style>