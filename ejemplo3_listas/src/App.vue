

<template>
  <h1>RENDERIZADO LISTAS</h1>
  <ul>
    <li v-for="dia in laborables">{{ dia }}</li>
  </ul>
  <h2>Array de objetos</h2>
  <ul>
    <li v-for="tarea in tareas">{{ tarea.nombre }} - <small> {{ tarea.prioridad }} </small></li>
  </ul>
  <ul>
    <li v-for="(tarea, index) in tareas">{{ index }} - {{ tarea.nombre }} - <small> {{ tarea.prioridad }} </small></li>
  </ul>
  <h2> Renderizar objeto</h2>
  <ul>
    <li v-for="(valor, clave, index) in objtAttr"> {{ index }} - {{ clave }} - {{ valor }}</li>
  </ul>
</template>

<script setup>
  const laborables=['lunes','martes','miercoles','jueves','viernes']

  const tareas =[
    {nombre: 'estudiar vue', prioridad: 'baja'},
    {nombre: 'estudiar laravel', prioridad: 'baja'},
    {nombre:'hacer la cma', prioridad:'alta'}
  ]
  
  const objtAttr={
    id:'contenedor',
    class:'rojo',
    style: 'background-color: green'
  }
</script>