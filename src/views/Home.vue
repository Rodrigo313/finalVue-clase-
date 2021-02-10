<template>
  <div class="inicio">
    <img alt="laLiga" src="https://upload.wikimedia.org/wikipedia/commons/6/6e/LaLiga_Santander_%282%29.svg">
    <Inicio msg="Temporada 2020-2021"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Inicio from '@/components/Inicio.vue'

export default {
  name: 'Home',
  components: {
    Inicio
  }
}
</script>

<style scoped>
  img{
    width: 1000px;
    height: 1000px;
  }
</style>
