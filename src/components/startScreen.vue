<script setup>
  import { ref } from 'vue'
  const emit = defineEmits(['start-quiz']);
  const topic = ref( '' );
</script>

<template>
  <section class="start-screen container">
    <h2>Ultimas noticias que impactaron los trades entre {{ topic }}</h2>
    <input v-model="topic" type="text" placeholder="monedas con las que esta haciendo trading">
    <button @click="emit('start-quiz', topic)" :disabled="!topic" >Buscar Informacion</button>
  </section>
</template>

