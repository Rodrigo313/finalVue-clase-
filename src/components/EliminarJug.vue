<template>
    <div class="compEliminar">
        <select v-model="name">
            <option :value="jugadores.name" v-for="(jugadores, nn) in arrayJugadores" :key="nn">{{jugadores.name}}</option>
        </select>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            arrayJugadores:[],
            name:''
        }
    },
    props:[
        "nombreEquipo"
    ],
    methods:{
        obtenerJugadores(nombre){
            axios.get("http://localhost:3000/players?team=" + nombre)
            .then(response =>{
            this.arrayJugadores = response.data;
            } )
        .catch(response => alert("Errores: " + response.status));
     } 
        },
        watch:{
            nombreEquipo(nuevo){ 
                this.arrayJugadores = this.obtenerJugadores(nuevo);
        }
    }
}
</script>

<style scoped>
</style>