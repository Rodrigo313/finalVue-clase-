<template>
    <div class="equipos">
        <h1>Equipos</h1>
        <table>
            <tr class="tdd" v-for="(equipos, index) in arrayEquipos" :key="index">
                <td> {{equipos.name}}
                    <span>
                        <ul v-for="(jugadores, index) in arrayJugadores" :key="index">
                            <li v-if="equipos.name == jugadores.team"> {{jugadores.name}} </li>
                        </ul>
                    </span>
                </td>
            </tr>
        </table>
    </div>
    <button @click="mostrarComp">Nuevo jugador</button>

    <div v-show="show">
        <NuevoJug/>
    </div>
</template>

<script>
import axios from "axios";
import NuevoJug from '@/components/NuevoJug.vue'
export default {
    data(){
        return{
            arrayEquipos:[],
            arrayJugadores:[],
            show:false
        }
    },
     created(){
        axios.get('http://localhost:3000/clubs')
        .then(response =>{
            this.arrayEquipos = response.data;
        } )
        .catch(response => alert("Errores: " + response.status)),
    
        axios.get('http://localhost:3000/players')
        .then(response =>{
            this.arrayJugadores = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    components:{
      NuevoJug
    },
    methods:{
        mostrarComp: function(){
            this.show = !this.show;
        }
    }
}
</script>

<style scoped>
</style>