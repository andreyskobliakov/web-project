<template>
  <form @submit.prevent="onSubmit" class="max-w-md mx-auto my-4 p-4 bg-white rounded-lg shadow-lg">
    <div class="mb-4">
      <custom-input name="login" class="mb-2">
        <input
          class="w-full px-4 py-2 text-lg border-none focus:outline-none focus:border-blue-500"
          :placeholder="placeholder"/>
      </custom-input>
    </div>
    <div class="mb-4">
      <custom-input type="password" name="password" class="mb-2">
        <input
          class="w-full px-4 py-2 text-lg border-none focus:outline-none focus:border-blue-500"
          :placeholder="placeholder"/>
      </custom-input>
    </div>
    <button class="w-full py-2 px-4 bg-blue-500 hover:bg-blue-600 text-white font-semibold rounded-full focus:outline-none focus:ring-2 focus:ring-blue-500">
      Submit
    </button>
  </form>
</template>


<script setup>
import { provide, ref } from "vue";
import CustomInput from "../Provide/CustomInput.vue";

const form = ref({
  login: "Name",
  password: ""
});


provide("formData", form);

const onSubmit = () => {
  console.log(form.value);
};
</script>

<style scoped>
</style>
