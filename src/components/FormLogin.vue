<template>
  <div class="min-h-screen flex items-center justify-center">
    <div class=" p-8 rounded shadow-md w-full max-w-md">
      <h2 class="text-2xl font-semibold text-center mb-4">FORM</h2>
      <form @submit.prevent="onSubmit">
        <div class="mb-4">
          <custom-input :modelValue="form.Login" class="mb-2"/>
        </div>
        <div class="mb-6">
          <custom-input :modelValue="form.password" type="password" class="mb-2" />
        </div>
        <div>
          <button type="submit" class=" hover:bg-blue-600 text-blue-400 py-2 px-4 rounded border border-blue-500 focus:outline-none focus:shadow-outline w-full">
            Submit
          </button>
        </div>
      </form>
    </div>
  </div>
</template>







<script setup>
import { ref, provide } from "vue";
import CustomInput from "./CustomInput.vue";

const form = ref({
  Login: "Name",
  password: "",
});

provide("formData", form);

const onSubmit = () => {
  console.log(form.value);
};
</script>
