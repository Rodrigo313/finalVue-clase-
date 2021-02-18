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
    <div>
        <Datos/>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            array:[]
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
    }
}
</script>

<style scoped>
.clasificacion{
    width: 1000px;
    float: right;
    margin-top: 100px;
}

.titulo{
  margin-right: 800px;
  float: left;
}
</style>
