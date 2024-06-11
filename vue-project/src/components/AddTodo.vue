<script setup lang="ts">
import { ref, defineEmits } from 'vue';

const todoText = ref('');

const handleSubmit = () =>{
  console.log(todoText.value);

  emit('createTodo', todoText.value);
  todoText.value = '';
}

const emit = defineEmits<{
 (e: 'createTodo', text: string): void
}>();

</script>

<template>
  <form @submit.prevent="handleSubmit">
      <input type="text" placeholder="Skriv här..." v-model="todoText"/>
      <button type="submit">Lägg till</button>
  </form>
</template>

<style scoped>

</style>