<template>
    
    <div class="container"> 
    <ul v-for="(tarea, index) in tareas" :key="index" >
        <li>{{tarea}}<button @click="emitirMensajeDeBorrar" v-bind:value="index">Eliminar</button></li>
    </ul>
    </div>
</template>

<script>
export default {
    name: "ListaTareas",
    props: {
        tareas:Array
    },
    methods:{
        emitirMensajeDeBorrar: function(event){
            let indiceBorrarTarea = event.target.value;
            event.target.checked = false;
            this.$emit("receptorIndexBorrarTarea",indiceBorrarTarea);
        }
    }
}
</script>

<style scoped>
.container  {
  width: 30rem;
  margin: 0 auto;
  text-align: left;
  margin-left: 33%;
}

button {
        width: 80px;
        height: 20px;
        border-radius: 10px;
        margin-left: 1rem;
        border: none;
    }

li {

    font-size: 20px;
}
</style>