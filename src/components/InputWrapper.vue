<template>
    <div class="form-control w-full max-w-xs mt-5 mb-5 justify-items-center">
      <label class="label">
        <span class="label-text" v-if="label">{{ label }}</span>
        <slot name="label-alt"></slot>
      </label>
      <input :type="type" :placeholder="placeholder" class="input input-sm input-bordered w-full max-w-xs mb-1 px-3 py-2 text-base border rounded-lg focus:outline-none focus:border-stone-950 transition duration-300 ease-in-out"
             v-model="inputValue" @focus="showError = true" @input="clearError" />
      <slot name="helper-text"></slot>
      <p v-if="showError" class="text-red-500 mb-5">{{ errorMessage }}</p>
    </div>
  </template>
  
  <script>
  import { defineProps, ref } from 'vue';
  
  export default {
    props: {
      label: String,
      placeholder: String,
      type: String,
    },
    setup(props) {
      const inputValue = ref("");
      const showError = ref(false);
  
      const errorMessage = "The field is not filled";
  
      const clearError = () => {
        showError.value = false;
      };
  
      return {
        inputValue,
        showError,
        errorMessage,
        clearError,
      };
    },
  };
  </script>
  