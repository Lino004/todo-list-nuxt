<template>
  <div class="flex items-center space-x-4 group min-h-[32px]">
    <input
      type="checkbox"
      class="app-checkbox"
      :id="`check-${index}`"
      @change="onChange"
      :checked="modelValue"
    />
    <input
      class="flex-1 border-none rounded-lg text-gray-900 text-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-1 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light"
      :value="content"
      type="text"
      placeholder="Content..."
    >
    <div class="w-8">
      <button type="button" class="rounded-md hidden group-hover:block w-full" @click="$emit('delete')">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
          <title>delete-outline</title>
          <path class="fill-red-500" d="M6,19A2,2 0 0,0 8,21H16A2,2 0 0,0 18,19V7H6V19M8,9H16V19H8V9M15.5,4L14.5,3H9.5L8.5,4H5V6H19V4H15.5Z" />
        </svg>
      </button>
    </div>
  </div>
</template>

<script lang="ts" setup>


  interface Props {
    content: string,
    modelValue: boolean,
    index: number,
  }
  interface Emit {
    (event: 'update:modelValue', payload: boolean): void;
    (event: 'delete'): void;
  }

  defineProps<Props>()
  const emit = defineEmits<Emit>();

  const onChange = (event: Event) => {
    emit('update:modelValue',(event.target as HTMLInputElement).checked)
  };
  
</script>
