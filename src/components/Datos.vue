<template>
  <div class="content">
      <table>
        <tr class="tdd" v-for="(cadaElemento, nn) in array" :key="nn">
          <td> {{cadaElemento.name}}</td>
          <td>{{cadaElemento.scores}}</td>
        </tr>
      </table>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      array:[]
    }
  },
   props:[
     "nombreEquipo"
   ],
   watch:{
        nombreEquipo(nuevo){ 
            this.array = this.sacarDatos(nuevo);
        }
    },
   methods:{
     sacarDatos(nombreEquipo){
      console.log("hijo recibe: " + nombreEquipo)
        axios.get('http://localhost:3000/players?team=' + nombreEquipo)
        .then(response =>{
          this.array = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
     }
   }
};
</script>

<style scoped>
</style>