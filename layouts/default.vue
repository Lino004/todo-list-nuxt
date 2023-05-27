<template>
  <section class="m-4 max-w-md mx-auto dark:bg-gray-900" :class="{dark: darkMode}">
    <slot />
  </section>
</template>

<script lang="ts" setup>
  import { useDarkMode } from '~/store/general';

  const darkMode = useDarkMode()
</script>
