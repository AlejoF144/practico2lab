<template>
    <!--Modal a mostrar en caso de presionarlo en infoButton-->
    <div class="modal">
        <div class="modal-inner">
            <h1>
                Más información
            </h1>
            <p>
                Nombre: {{ juegosInfo.nombre }} <br>
                Estado: {{ juegosInfo.estado }} <br>
                Plataforma: {{ juegosInfo.plataforma }} <br>
                Puntaje: {{ juegosInfo.puntaje }} <br>
            </p>
            <button class="close-btn" @click="close()">Cerrar</button>
        </div>
    </div>
</template>

<script setup>
import { defineEmits, defineProps } from "vue"
// Emit, emitirá una señal (por así decirlo) que será escuchada en infoButton, cerrará el modal
const emitEvent = defineEmits(["close"]) // Nombre de la señal a escuchar, no estoy muy seguro 

defineProps({
    juegosInfo: Array
})

function close() {
    emitEvent("close")
}

</script>


<style scoped>
.modal {
    background-color: rgba(82, 82, 82, 0.9);
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    /* Centrar el modal */
    z-index: 10;
    padding: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal-inner {
    text-align:center;
    background-color: aquamarine;
    color: black;
    position: relative;
    max-width: 50%;
    padding-top: 40px;
    padding-bottom: 40px;
    padding-left: 160px;
    padding-right: 160px;
    border-radius: 8px;
}


.modal .close-btn {
    background-color: #FF5722;
    /* Color rojo para el botón de cierre */
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    outline: none;
    /* Quitar el borde de enfoque predeterminado */
    transition: background-color 0.3s ease;
    /* Animación de hover */
}

.modal .close-btn:hover {
    background-color: #C42700;
    /* Color rojo más oscuro al pasar el cursor */
}
</style>