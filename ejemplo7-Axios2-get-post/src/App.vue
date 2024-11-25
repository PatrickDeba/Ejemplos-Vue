<template>
<h1>AXIOS GET POST</h1>
<h2>Gestion de Usuarios</h2>
<form @submit.prevent="agregarTarea">
  <input type="text" v-model="nuevaTarea.title">
  <button type="submit">Agregar Tarea</button>
</form>

<br>
<h2>Listado de tareas</h2>
<ul>
  <li v-for="tarea in tareas" :key="tarea.id">
    {{tarea.title}}
  </li>
</ul>

</template>

<script setup>
  import axios from 'axios'
  import { ref, onMounted } from 'vue'

  const tareas=ref([]);
  const nuevaTarea=ref({title:'', completed:false});

  onMounted( () => {
    cargarTareas()
  })

  const cargarTareas = async () =>{
    try{
      const response = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      tareas.value = response.data
    } catch (error){
      console.error("El error devuelto es: ", error)
    }
  }

  const agregarTarea = async () =>{
    try{
      const response = await axios.post('https://jsonplaceholder.typicode.com/todos', nuevaTarea.value);
      console.log(response.data)
      tareas.value.push(response.data);
      nuevaTarea.value = ({title:'', completed:false});
    } catch (error){
      console.error("El error devuelto es: ", error)
    }
  }
</script>
