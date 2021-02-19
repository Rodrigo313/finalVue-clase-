<template>
    <div class="equipos">
        <table>
            <tr class="tdd" v-for="(equipos, index) in arrayEquipos" :key="index">
                <td> {{equipos.name}}</td>
            </tr>
            <tr v-for="(jugadores, index) in arrayJugadores" :key="index">
                <td>{{jugadores.name}}</td>
            </tr>
        </table>
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
     created(){
        axios.get('http://localhost:3000/clubs'),
        axios.get('http://localhost:3000/players')
        .then(response =>{
            this.arrayEquipos = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    name: 'Equipos',
}
</script>

<style scoped>

</style>