<script setup lang="ts">
import TodoPrint from './TodoPrint.vue'
import type { Todo } from '@/models/Todo';
import { defineProps, defineEmits } from 'vue';

interface ITodosProps {
    todos: Todo[];
}

defineEmits<{
 (e: 'toggleTodo', id: number): void;
 (e: 'removeTodo', id: number): void
}>();

const props = defineProps<ITodosProps>();

console.log(props.todos.length);


</script>

<template>
<div>
    <TodoPrint 
      v-for="todo in todos" 
      :key="todo.id" 
      :todo="todo" 
      @change-todo="(id: number) => $emit('toggleTodo', id)" 
      @delete-todo="(id: number) => $emit('removeTodo', id)"
      ></TodoPrint>
</div>
</template>
