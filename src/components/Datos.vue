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
export default {
   props:[
     "nombreEquipo"
   ],
      created(nombreEquipo){
        console.log("lmao")
        axios.get('http://localhost:3000/players?team=' + nombreEquipo)
        .then(response =>{
          this.array = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    }
};
</script>

<style scoped>

</style>