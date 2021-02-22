<template>
    <div class="clasificacion">
      <h1 class="titulo">Jugadores</h1>
        <table class="tabla">
            <tr class="tdd" v-for="(cadaElemento, nn) in array" :key="nn" @click="pasarNombre(cadaElemento.name)">
                <td> {{cadaElemento.name}}</td>
                <td>{{cadaElemento.points}}</td>
            </tr>
        </table>
    </div>
    <div class="componente">
        <DatosJugadores :nombreEquipo="variable"></DatosJugadores>
    </div>
    <div class="datosJugador">
        <DatosJugadores :id="id"></DatosJugadores>
        <DatosJugadores :team="team"></DatosJugadores>
        <DatosJugadores :scores="scores"></DatosJugadores>
    </div>
</template>

<script>
import DatosJugadores from '@/components/DatosJugadores.vue'
import axios from "axios";
export default {
    data(){
        return{
            array:[],
            variable: '',
            id:'',
            team:'',
            scores:''
        }
    },
    created(){
        axios.get('http://localhost:3000/clubs')
        .then(response =>{
            this.array = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    name: 'Clasificacion',
    methods:{
        pasarNombre(dato){
            this.variable = dato;
        }
    },
    components:{
        DatosJugadores
    }
}
</script>

<style scoped>
    .clasificacion{
        margin-right: 700px;
    }
</style>
