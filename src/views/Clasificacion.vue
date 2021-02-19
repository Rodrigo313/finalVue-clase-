<template>
    <div class="clasificacion">
      <h1 class="titulo">Clasificación</h1>
        <table class="tabla">
            <tr class="tdd" v-for="(cadaElemento, nn) in array" :key="nn" @click="pasarNombre(cadaElemento.name)">
                <td> {{cadaElemento.name}}</td>
                <td>{{cadaElemento.points}}</td>
            </tr>
        </table>
    </div>
    <div class="componente">
        <Datos :nombreEquipo="variable"></Datos>
    </div>
</template>

<script>
import Datos from '@/components/Datos.vue'
import axios from "axios";
export default {
    data(){
        return{
            array:[],
            variable: ''
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
            console.log("padre pasa este dato: " + dato)
            this.variable = dato;
        }
    },
    components:{
        Datos
    }
}
</script>

<style scoped>
.clasificacion{
    width: 450px;
    height: 1000px;
    background-color: cadetblue;
    float: right;
    margin-top: 100px;
    float: left;
}
.componente{
    background-color: yellow;
    width: 450px;
    height: 1000px;
    float: right;
}
</style>