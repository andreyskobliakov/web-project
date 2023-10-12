<template>
  <VeeForm v-slot="{ submitForm, isSubmitting }" :validation-schema="schema" as="div">
    <form @submit="submitForm" class="max-w-md mx-auto p-6 mt-8 bg-white rounded-lg shadow-lg">
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
      <button type="submit" class="btn btn-info" :disabled="isSubmitting">
        {{ isSubmitting ? 'Submitting...' : 'Submit' }}
      </button>
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

// Дополнительные улучшения

const messages = {
  email: {
    required: "Введите адрес электронной почты",
    email: "Введите действительный адрес электронной почты",
  },
  password: {
    required: "Введите пароль",
    min: "Пароль должен быть не менее 8 символов",
  },
};

const isLoading = ref(false);

function submitForm() {
  // Отправка формы на сервер
}
</script>
