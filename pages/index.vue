<template>
  <header class="flex items-center justify-between border-b pb-4 mb-4 dark:bg-gray-900">
    <div>
      <h1 class="text-3xl font-bold dark:text-white"> To Do </h1>
      <p class="font-medium dark:text-white"> Note... </p>
    </div>
    <div class="space-x-2 flex">
      <button type="button" class="bg-blue-200 p-2 rounded-md w-10" @click="addTask">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>plus</title><path d="M19,13H13V19H11V13H5V11H11V5H13V11H19V13Z" /></svg>
      </button>
    </div>
  </header>
  <section class="space-y-4 dark:bg-gray-900">
    <AppTask
      v-for="(task) in tasks" :key="task.id" :index="task.id"
      :content="task.content" v-model="task.ckeck"
      @delete="deleteTask(task.id)"
    />
  </section>
</template>

<script lang="ts" setup>
import { reactive } from 'vue'
import { useDarkMode } from '~/store/general';

interface Task {
  ckeck: boolean,
  content: string,
  id: number,
}

const tasks = reactive<Task[]>([
  { ckeck: false,  content: 'Indeterminate checkbox', id: 0 },
])
const darkMode = useDarkMode()

const deleteTask = (id: number) => {
  const index = tasks.findIndex(t => t.id === id);
  if (index !== -1) tasks.splice(index, 1);
}
const addTask = () => {
  tasks.push({ ckeck: false,  content: '', id: tasks.length});
}
</script>
