<template>
    <div class="listFilter">
        <h3>Lista de videojuegos</h3>
        <div class="search-container">
            <div class="input-group">
                <label for="buscar-nombre">Nombre:</label>
                <input type="text" id="buscar-nombre">
            </div>

            <div class="input-group">
                <label for="buscar-plataforma">Plataforma:</label>
                <select id="buscar-plataforma">
                    <option value="PC">PC</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Playstation">Playstation</option>
                </select>
            </div>

            <div class="input-group">
                <label for="buscar-estado">Estado:</label>
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
    </div>
</template>

<script setup>

</script>