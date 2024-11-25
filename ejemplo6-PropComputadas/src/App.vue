<template>
  <h1>PROPIEDADES COMPUTADAS</h1>
  <hr>
  <input type="text" placeholder="nombre" v-model="nombre">
  <input type="text" placeholder="apellido" v-model="apellido">
  <input type="number" placeholder="Año de Nacimiento" v-model="birthYear">

  <p>Nombre Completo {{ nombreCompleto }}</p>
  <p>Años: {{ edad }}</p>
</template>

<script>
 import { computed } from 'vue'

 const nombre = ref('')
  const apellido = ref('')
  const birthYear = ref(1900)

  const nombreCompleto = computed(() => 
    `${nombre.value} ${apellido.value}`
  )

  const edad = computed(() => {
    let añoActual = new Date().getFullYear();
    return añoActual - birthYear.value
  })
  

</script>