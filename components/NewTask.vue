<script setup lang="ts">
import type { Task } from '~~/types';
defineProps<{
  task: Task;
}>();
</script>

<template>
  <div :title="task.createdAt.toLocaleDateString()">
    <span>
      {{ task.title }}
    </span>
  </div>
</template>
