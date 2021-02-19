<template>
    <div class="partido">
        <form class="formulario">
            <fieldset>
                <legend>Nuevo partido</legend>
                <select class="local">
                    <option value="0">Equipo local</option>
                    <option v-for="(cadaElemento, nn) in array" :key="nn">{{cadaElemento.name}}</option>
                </select><br><br>
                <select class="visitante">
                    <option value="0">Equipo visitante</option>
                    <option v-for="(cadaElemento, nn) in array" :key="nn">{{cadaElemento.name}}</option>
                </select><br><br>
                <input class="boton" type="submit" value="Nuevo partido">
            </fieldset>
        </form>
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
    name: 'Partido',
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
</style>