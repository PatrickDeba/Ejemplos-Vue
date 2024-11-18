<template>
  <h1>VACIO

  </h1>
  <br>
  <p :class="contador < 0 ? 'rojo' : 'verde' ">Contador: {{ contador }}</p>
  <button @click="incrementar">+</button>
  <button @click="decrementar">-</button>
  <button @click="resetear">Resetear</button>
</template>

<script setup>
  import { ref } from 'vue';
  const contador = ref(0);
  const incrementar = () => {
    contador.value++;
  }
  const decrementar = () => {
    contador.value--;
  }
  const resetear = () => {
    contador.value = 0;
  }
</script>

