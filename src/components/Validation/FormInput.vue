<template>
    <div class="mb-4">
      <label :for="name" class="block text-sm font-medium text-gray-700">{{ label }}</label>
      <slot></slot>
      <span v-if="error" class="text-red-500 text-sm">{{ error }}</span>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      label: String,
      name: String,
      error: String,
    },
  };
  </script>
  