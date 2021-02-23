<template>
    <div class="eliminacion">
        <form>
            <fieldset>
                <legend>Eliminar Jugador</legend>
                <select class="equipos" v-model="name">
                    <option :value="equipos.name" v-for="(equipos, nn) in arrayEquipos" :key="nn">{{equipos.name}}</option>
                </select>
                    <EliminarJug class="jugadores" :nombreEquipo="name"></EliminarJug>
                <button class="boton" @click="borrarJugador()">Eliminar Jugador</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
import axios from "axios";
import EliminarJug from '@/components/EliminarJug.vue'
export default {
    data(){
        return{
            arrayEquipos:[],
            arrayJugadores:[],
            id:'',
            name:'',
            team:'',
            scores:''
        }
    },
    methods:{
        equipos(){
            axios.get('http://localhost:3000/clubs')
            .then(response =>{
                this.arrayEquipos = response.data;
            } )
            .catch(response => alert("Errores: " + response.status));
        },
        jugadores(){
            axios.get('http://localhost:3000/players')
            .then(response =>{
                this.arrayJugadores = response.data;
            } )
            .catch(response => alert("Errores: " + response.status));
        },
        borrarJugador(){
            axios.delete("http://localhost:3000/players/" + this.id);
        }
    },
    created(){
            this.equipos();
            this.jugadores();
    },
    components:{
        EliminarJug
    }
}
</script>

<style scoped>
    .equipos{
        float: left;
        margin-top: 200px;
    }
    .jugadores{
        float: left;
        margin-top: 200px;
        margin-left: 50px;
    }
    .boton{
        float: left;
        margin-top: 200px;
        margin-left: 50px;
    }
</style>