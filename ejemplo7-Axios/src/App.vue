<template>
<h1>Uso simple de Axios</h1>
<h2>Usuarios traidos de jsonplaceholder</h2>

<ul>
  <li v-for="usuario in users" :key="users.id">
    {{usuario.name}}
  </li>
</ul>
</template>

<script setup>
import axios from 'axios'
import { ref, onMounted } from 'vue'

const users = ref([])

onMounted( () => {
  cargarUsers()
})



const cargarUsers = async () =>{
  try{
    const response = await axios.get('https://jsonplaceholder.typicode.com/users')
    console.log(response)
    users.value = response.data
  } catch (error){
    console.error("El error devuelto es: ", error)
  }
}

</script>
