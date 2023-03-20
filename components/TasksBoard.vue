<script setup lang="ts">
import type { Column, Task } from '~~/types';
import { nanoid } from 'nanoid';
import draggable from 'vuedraggable';

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
      {
        id: nanoid(),
        title: 'Make an appointment with client',
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
  <div>
    <draggable
      v-model="columns"
      group="columns"
      item-key="id"
      :animation="550"
      handle=".drag-handle"
      class="flex gap-4 overflow-x-auto items-start"
    >
      <template #item="{ element: column }: { element: Column }">
        <div class="column bg-gray-300 p-5 rounded min-w-[250px]">
          <header class="font-bold mb-4 flex items-center">
            <DragHandle />
            {{ column.title }}
          </header>
          <draggable
            v-model="column.tasks"
            group="tasks"
            item-key="id"
            :animation="150"
            handle=".drag-handle"
          >
            <template #item="{ element: task }: { element: Task }">
              <NewTask :task="task" />
            </template>
          </draggable>

          <footer>
            <button class="text-gray-500">+ Add a Card</button>
          </footer>
        </div>
      </template>
    </draggable>
  </div>
</template>
