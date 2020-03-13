<template>
    <div id="main">
            <span class="titulo">{{ message }}</span>
        <br>
        <br>
            <label>Ingrese Tarea: </label>
            <input type="text" v-model="tarea"/>

            <button @click="guardarTarea">Ingresar tarea</button>
            <p v-if="mostrar">{{nombre}}</p>
        <br>
        <br>
            <label>Lista de Tareas:</label>
        <lista-tareas @receptorIndexBorrarTarea="borrarTarea" :tareas="tareas" > </lista-tareas>
          
    </div>
</template>

<script>
import ListaTareas from "./components/ListaTareas.vue"
    export default {
        data(){
            return{
                message:"Agenda de Tareas",
                tarea:"",
                tareas:[],
                mostrar:false
            }
        },
        methods: {
            mostrarTarea: function(){
                this.mostrar = !this.mostrar;
            },
            guardarTarea: function(){
                if(this.tarea !== ""){
                    this.tareas.push(
                        this.tarea
                    );
                }
                this.tarea="";
            },
            borrarTarea: function(index){
                this.tareas.splice(index, 1);
                
            }

        },
        components:{
            ListaTareas
        }      
    };
</script>
<style scoped>

    * {
    margin: 0 auto;
    border: 0;
    padding: 0;
    font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif
    }
    #main {
        margin-top: 40px;
        text-align: center;
        font-size: 25px;
        font-family: 'Calibri', sans-serif;
        background: rgb(85, 255, 210);
        color: rgb(91, 91, 91);
        padding: 5em;
        width: 40rem;
        height: 20rem; 
    }

   

    input {
        width: 180px;
        height: 25px;
        border-radius: 10px;
    }
    button {
        width: 100px;
        height: 25px;
        border-radius: 10px;

    }
    .titulo {
        font-size: 30px;
    }


</style>