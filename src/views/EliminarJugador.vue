<template>
    <div class="eliminacion">
        <select class="equipos">
            <option value="0">Equipos</option>
            <option v-for="(equipos, nn) in arrayEquipos" :key="nn">{{equipos.name}}</option>
        </select><br><br>
        <select class="jugadores">
            <option value="0">Jugadores</option>
            <option v-for="(jugadores, nn) in arrayJugadores" :key="nn">{{jugadores.name}}</option>
        </select><br><br>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            arrayEquipos:[],
            arrayJugadores:[]
        }
    },
    methods:{
        equipos(){
            axios.get('http://localhost:3000/clubs')
            .then(response =>{
                this.arrayEquipos = response.data;
            } )
            .catch(response => alert("Errores: " + response.status));
        },
        jugadores(){
            axios.get('http://localhost:3000/players')
            .then(response =>{
                this.arrayJugadores = response.data;
            } )
            .catch(response => alert("Errores: " + response.status));
        },
    },
    created(){
            this.equipos();
            this.jugadores();
    },
    name: 'EliminarJugador',
}
</script>

<style scoped>
    .equipos{
        float: left;
        margin-top: 200px;
    }
    .jugadores{
        float: left;
        margin-top: 200px;
    }
    .boton{
        float: left;
    }
</style>