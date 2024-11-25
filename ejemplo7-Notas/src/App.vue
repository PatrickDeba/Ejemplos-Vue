<template>
  <h1>NOTAS</h1>
  <hr>
  <form @submit.prevent="addNota"> <!-- Evita que se recargue la página -->
    <input 
      type="text" 
      placeholder="nota" 
      v-model="newNota" 
      @keydown.enter="addNota"> 
    <!-- @keydown.enter permite que al presionar la tecla Enter se ejecute la función addNota -->
    <button type="submit">Agregar</button>
  </form>
  <br>
  <h2>Lista de Notas</h2>
  <ul>
    <!-- v-for es una directiva de Vue que permite recorrer un array -->
    <li v-for="(nota, index) in ArrayNotas" :key="nota.id"> 
      <input type="text" 
      v-model="nota.text" 
      :disabled="!nota.editando">

      <button @click="editarNota(nota)">{{nota.editando? 'Confimar':'Editar'}}</button> <!-- Si nota.editando es True Confirmar, si no Editar-->
      <button @click="deleteNota(index)">Eliminar</button>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue'; // Importa la función ref de Vue

    let inhabilitado = "true";

    const ArrayNotas = ref([]); // Define el array de notas
    const newNota = ref(''); // Define la nueva nota

    const addNota = () => {
        ArrayNotas.value.push({ id:Date.now(), text: newNota.value, editando: false }); // Agrega una nueva nota al array
        newNota.value = ''; // Limpia el input
    };

    const deleteNota = (index) => {
      ArrayNotas.value.splice(index, 1); // Elimina la nota en el índice especificado
    };

    const editarNota = (nota) => {
     nota.editando = !nota.editando;
    };
</script>
