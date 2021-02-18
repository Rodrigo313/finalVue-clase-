<template>
  <div id="nav">
    <router-link to="/">Inicio</router-link> |
    <router-link to="/clasificacion">Clasificación</router-link> |
    <router-link to="/jornadas">Jornadas</router-link> |
    <router-link to="/partido">Nuevo Partido</router-link> <br>
    <router-link to="/equipos">Equipos</router-link> |
    <router-link to="/jugadores">Jugadores</router-link> |
    <router-link to="/nuevoJugador">Nuevo Jugador</router-link> |
    <router-link to="/eliminarJugador">Eliminar Jugador</router-link>
  </div>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  float: left;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
