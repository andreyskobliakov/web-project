<template>
  <VeeForm v-slot="{ submitForm, isSubmitting }" :validation-schema="schema" as="div">
    <form @submit="submitForm()" class="max-w-md mx-auto p-6 mt-8 bg-white rounded-lg shadow-lg">
      <div class="mb-4">
        <label for="email" class="block text-gray-600">Email:</label>
        <Field name="email" type="email" id="email" class="mt-1 p-2 border rounded-md focus:ring focus:ring-blue-400 w-full" />
        <ErrorMessage name="email" class="text-red-500" />
      </div>
      <div class="mb-4">
        <label for="password" class="block text-gray-600">Password:</label>
        <Field name="password" type="password" id="password" class="mt-1 p-2 border rounded-md focus:ring focus:ring-blue-400 w-full" />
        <ErrorMessage name="password" class="text-red-500" />
      </div>
      <div class="mb-4">
        <button
          type="submit"
          class="btn btn-info"
          :disabled="isSubmitting"
        >
          {{ isSubmitting ? 'Submitting...' : 'Submit' }}
        </button>
      </div>
    </form>
  </VeeForm>
</template>

<script setup>
import { Form as VeeForm, Field, ErrorMessage } from 'vee-validate';
import { ref } from 'vue';
import * as yup from 'yup';

const schema = yup.object({
  email: yup.string().required().email(),
  password: yup.string().required().min(8),
});


const isLoading = ref(false);
const errors = ref({});

function submitForm() {
  isLoading.value = true;

  fetch('/login', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      email: formValues.email,
      password: formValues.password,
    }),
  })
    .then(response => response.json())
    .then(data => {
      
      if (data.success) {
        window.location.href = '/';
      } else {
       
        errors.value = data.errors;
      }
    })
    .catch(error => {
      console.log(error);
    })
    .finally(() => {
      isLoading.value = false;
    });
}
</script>
