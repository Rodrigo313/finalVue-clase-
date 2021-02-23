<template>
    <div class="partido">
        <form class="formulario">
            <fieldset>
                <legend>Nuevo partido</legend>
                <select class="local" v-model="team1">
                    <!--<option value="0">Equipo local</option>-->
                    <option v-for="(cadaElemento, nn) in array" :key="nn">{{cadaElemento.name}}</option>
                </select><br><br>
                <select class="visitante" v-model="team2">
                    <!--<option value="0">Equipo visitante</option>-->
                    <option v-for="(cadaElemento, nn) in array" :key="nn">{{cadaElemento.name}}</option>
                </select><br><br>
                <input class="fecha" type="date" v-model="date"><br><br>
                <input class="jornada" type="text" placeholder="Jornada" v-model="round"><br><br>
                <button @click="envioForm()" class="boton">Nuevo partido</button>
            </fieldset>
        </form>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            array:[],
            round:'',
            date:'',
            team1:'',
            team2:''
        }
    },
    created(){
        axios.get('http://localhost:3000/clubs')
        .then(response =>{
            this.array = response.data;
        } )
        .catch(response => alert("Errores: " + response.status));
    },
    methods:{
    envioForm(){
        let post = {
            round:this.round,
            date:this.date,
            team1:this.team1,
            team2:this.team2
        };
        axios.post("http://localhost:3000/matches", post)
    },
    }
}
</script>

<style scoped>
    .formulario{
        margin-left: 500px;
        
    }
    .local{
        float: left;
    }
    .visitante{
        float: left;
    }
    .boton{
        float: left;
    }
    .fecha{
        float: left;
    }
    .jornada{
        float: left;
    }
</style>