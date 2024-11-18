<template>
  <h1>VACIO

  </h1>
  <br>
  <button v-on:click="mensajeConsola">Pulsame</button>
  <button v-on:click="mensajeConsola">Pulsame otro</button>
  </template>

  <form @submit.prevent="submitPulsado">
    <button type="submit">Enviar</button>
  </form>

  <script setup>
const mensajeConsola=()=>{
  alert("Hola mundo");
}

function teclaPulsada(event){
  console.log(event.key);
}

const submitPulsado = () => {
  alert("Has pulsado enter");
}

</script>

