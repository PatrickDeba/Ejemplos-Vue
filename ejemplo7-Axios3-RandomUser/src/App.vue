<template>
  <div>
    <h1>Personas</h1>
    <!-- Selector para elegir el género -->
    <select v-model="generoSeleccionado">
      <option value="">Selecciona</option>
      <option value="male">Hombre</option>
      <option value="female">Mujer</option>
    </select>

    <br>
    <br>

    <!-- Lista de personas filtrada por género -->
    <div v-for="persona in personasFiltradas" :key="persona.login.uuid">
      <img :src="persona.picture.medium">
      {{ persona.name.first }} {{ persona.name.last }}
    </div>
  </div>
</template>

<script setup>
import axios from 'axios'
import { ref, onMounted, computed } from 'vue'

const personas = ref([]);
const generoSeleccionado = ref(""); // Género seleccionado (vacío por defecto)

// Cargar personas al montar el componente
onMounted(() => {
  cargarPersonas();
});

// Función para obtener las personas desde la API
const cargarPersonas = async () => {
  try {
    const response = await axios.get('https://randomuser.me/api/?results=8');
    personas.value = response.data.results; // Accede correctamente a los resultados
  } catch (error) {
    console.error("El error devuelto es: ", error);
  }
};

// Computed para filtrar personas según el género seleccionado
const personasFiltradas = computed(() => {
  if (generoSeleccionado.value === "") {
    return personas.value; // Si no hay género seleccionado, muestra todas las personas
  }
  return personas.value.filter(persona => persona.gender === generoSeleccionado.value);
});
</script>
