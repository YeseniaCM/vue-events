<script setup lang="ts">
import type { Todo } from '@/models/Todo';
import { defineProps } from 'vue';


type TodoPrintProps = {
    todo: Todo;
}
defineProps<TodoPrintProps>();

defineEmits<{
 (e: 'changeTodo', id: number): void;
 (e: 'deleteTodo', id: number): void
}>();

</script>

<template>
<div>
    <h4 :class="todo.done ? 'done' : ''">{{ todo.text }}</h4>
        <button @click="$emit('changeTodo' , todo.id)">Ändra</button>
        <button @click="$emit('deleteTodo', todo.id)">Ta bort</button>
</div>
</template>

<style scoped>
.done{
    text-decoration: line-through;
}
</style>
