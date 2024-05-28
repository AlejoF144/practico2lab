<template>
    <div class="appContainer">
        <h1>Administración de videojuegos</h1>
        <div class="form-container">
            <div class="input-group">
                <label for="nombre">Nombre:</label>
                <input type="text" id="nombre">
            </div>

            <div class="input-group">
                <label for="plataforma">Plataforma:</label>
                <select id="plataforma">
                    <option value="PC">PC</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Playstation">Playstation</option>
                </select>
            </div>

            <div class="input-group">
                <label for="estado">Estado:</label>
                <select id="estado">
                    <option value="Pendiente">Pendiente</option>
                    <option value="Jugando">Jugando</option>
                    <option value="Completado">Completado</option>
                </select>
            </div>

            <div class="input-group">
                <label >Calificación:</label>
                <select id="calificacion">
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                    <option value="7">7</option>
                    <option value="8">8</option>
                    <option value="9">9</option>
                    <option value="10">10</option>
                </select>
            </div>
        </div>

        <button>Registrar juego</button>
    </div>
</template>
<script setup>

</script>

<style scoped>
.appContainer {
    margin: 20px;
    padding: 20px;
    text-align: center;

}

input[type="text"],
input[type="number"],
select {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3;
}
</style>