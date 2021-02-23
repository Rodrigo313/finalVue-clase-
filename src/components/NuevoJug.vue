<template>
    <div class="nuevoJugador">
        <form>
            <fieldset>
                <legend>Nuevo jugador</legend>
                <input class="nombre" type="text" placeholder="nombre jugador" v-model="name"><br><br>
                <input class="equipo" type="text" placeholder="equipo" v-model="team"><br><br>
                <input class="goles" type="number" placeholder="goles" v-model="scores"><br><br>
                <button class="boton" @click="enviarDatos()">Enviar</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            name: '',
            team: '',
            scores: ''
        }
    },
    methods:{
        enviarDatos(){
            let datosJugador = {
                name:this.name,
                team:this.team,
                scores: parseInt(this.scores)
            };
            axios.post("http://localhost:3000/players", datosJugador); 
        }
    },
}
</script>

<style scoped>
    .nombre{
        float: left;
    }
    .equipo{
        float: left;
    }
    .goles{
        float:left;
    }
    .boton{
        float: left;
    }
</style>