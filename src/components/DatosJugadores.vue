<template>
  <div class="content">
      <table>
        <tr class="tdd" v-for="(cadaElemento, nn) in array" :key="nn">
          <td @click="infoJugador(cadaElemento.id,cadaElemento.name,cadaElemento.team,cadaElemento.scores)"> {{cadaElemento.name}}</td>
        </tr>
      </table>
        <div class="infoJ" v-if="name!=''">
            <ul v-for="(cadaElemento, nn) in array" :key="nn">
                <li>{{cadaElemento.name}}</li>
                <li>{{cadaElemento.team}}</li>
                <li>Goles: {{cadaElemento.scores}}</li>
            </ul>
            <input type="number" placeholder="numeroGoles" v-model="anadirGol">
            <button @click="pasarDatos()">Añadir goles</button>
            <button @click="borrarJugador()">Eliminar jugador</button>
        </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      array:[],
      id:'',
      name:'',
      team:'',
      scores:'',
      anadirGol:''
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
        axios.get('http://localhost:3000/players?team=' + nombreEquipo)
        .then(response =>{
          this.array = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
     },
    infoJugador(id,name,team,scores){
        this.id = id;
        this.name = name;
        this.team = team;
        this.scores = scores;
    },     
     pasarDatos(){
         let post = {
            id:this.id,
            name:this.name,
            team:this.team,
            scores: parseInt(this.scores) + parseInt(this.anadirGol)
        };
        axios.put("http://localhost:3000/players/" + this.id, post)
     },
     borrarJugador(){
        axios.delete("http://localhost:3000/players" + this.id);
     }
   }
};
</script>

<style scoped>
    .content{
        float: right;
        margin-right: 500px;
    }
</style>