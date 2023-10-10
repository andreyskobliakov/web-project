<template>
    <form @submit.prevent="submitForm" class="w-96 mx-auto mt-8 p-6 bg-white rounded-lg shadow-lg">
      <FormInput label="Username" name="username" :error="errors.username">
        <input
          type="text"
          v-model="formData.username"
          @input="clearError('username')"
          :class="{ 'border-red-500': errors.username }"
          class="mt-1 p-2 border rounded-md focus:ring focus:ring-blue-400 w-full"
        />
      </FormInput>
  
      <FormInput label="Password" name="password" :error="errors.password">
        <input
          type="password"
          v-model="formData.password"
          @input="clearError('password')"
          :class="{ 'border-red-500': errors.password }"
          class="mt-1 p-2 border rounded-md focus:ring focus:ring-blue-400 w-full"
        />
      </FormInput>
  
      <FormInput label="Date of Birth" name="birthdate" :error="errors.birthdate">
        <input
          type="date"
          v-model="formData.birthdate"
          @input="clearError('birthdate')"
          :class="{ 'border-red-500': errors.birthdate }"
          class="mt-1 p-2 border rounded-md focus:ring focus:ring-blue-400 w-full"
        />
      </FormInput>
  
      <button type="submit" class="btn btn-info">Register</button>
    </form>
  </template>
  
  
  <script setup>
  import { ref } from 'vue';
  import * as yup from 'yup';
  import FormInput from './FormInput.vue';
  
  const formData = {
    username: '',
    password: '',
    birthdate: '',
  };
  
  const errors = ref({});

  
  const validationSchema = yup.object().shape({
    username: yup.string().required('Username is required').min(5, 'Username must be at least 5 characters long'),
    password: yup.string().required('Password is required').min(5, 'Password must be at least 5 characters long'),
    birthdate: yup.date().required('Date of Birth is required').test('is-18-years-old', 'You must be at least 18 years old', function (value) {
      const today = new Date();
      const birthdate = new Date(value);
      const age = today.getFullYear() - birthdate.getFullYear();
      return age >= 18;
    }),
  });
  
  async function submitForm() {
    try {
      await validationSchema.validate(formData, { abortEarly: false });
      alert('Registration successful!');
    } catch (error) {
      if (error instanceof yup.ValidationError) {
        const validationErrors = {};
        error.inner.forEach((err) => {
          validationErrors[err.path] = err.message;
        });
        errors.value = validationErrors;
      }
    }
  }
  
  function clearError(fieldName) {
    if (errors.value[fieldName]) {
      if (formData[fieldName].length >= 5) {
        errors.value[fieldName] = '';
      }
    }
  }
  </script>
  