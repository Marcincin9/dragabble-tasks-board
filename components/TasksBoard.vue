<script setup lang="ts">
import type { Column } from '~~/types';
import { nanoid } from 'nanoid';
const columns = ref<Column[]>([
  {
    id: nanoid(),
    title: 'Backlog',
    tasks: [
      {
        id: nanoid(),
        title: 'Create invoice for client',
        createdAt: new Date(),
      },
      {
        id: nanoid(),
        title: 'Send quotation to the client',
        createdAt: new Date(),
      },
    ],
  },
  { id: nanoid(), title: 'In Progress', tasks: [] },
  { id: nanoid(), title: 'Waiting for approve', tasks: [] },
  { id: nanoid(), title: 'Complete', tasks: [] },
]);
</script>

<template>
  <div v-for="column in columns" :key="column.id">
    <header>
      {{ column.title }}
    </header>
    <p v-for="task in column.tasks" :key="task.id">
      {{ task.title }}
    </p>
  </div>
</template>
