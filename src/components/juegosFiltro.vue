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
</template>

<script setup>

</script>

<style scoped></style>