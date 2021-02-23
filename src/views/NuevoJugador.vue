<template>
    <div class="nuevoJugador">
        <NuevoJug></NuevoJug>
    </div>
</template>

<script>
import NuevoJug from '@/components/NuevoJug'
export default {
    components:{
        NuevoJug
    }
}
</script>

<style scoped>
    .nombre{
        float: left;
    }
    .equipo{
        float: left;
    }
    .goles{
        float:left;
    }
    .boton{
        float: left;
    }
</style>