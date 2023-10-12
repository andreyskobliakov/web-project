<template>
  <form @submit.prevent="submitForm" class="w-96 mx-auto mt-8 p-6 bg-white rounded-lg shadow-lg">
    <FormInput label="Username" name="username" :error="errors.username">
      <input
        type="text"
        v-model="formData.username"
        @input="validateField('username')"
        :class="{ 'border-red-500': errors.username }"
        class="mt-1 p-2 border rounded-md focus:ring focus:ring-blue-400 w-full"
      />
    </FormInput>

    <FormInput label="Password" name="password" :error="errors.password">
      <input
        type="password"
        v-model="formData.password"
        @input="validateField('password')"
        :class="{ 'border-red-500': errors.password }"
        class="mt-1 p-2 border rounded-md focus:ring focus:ring-blue-400 w-full"
      />
    </FormInput>

    <FormInput label="Date of Birth" name="birthdate" :error="errors.birthdate">
      <input
        type="date"
        v-model="formData.birthdate"
        @input="validateField('birthdate')"
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
import FormInput from '../../components/Validation/FormInput.vue';

const formData = {
  username: '',
  password: '',
  birthdate: '',
};

const errors = ref({ username: '', password: '', birthdate: '' });

const validationSchema = yup.object().shape({
  username: yup.string().required('Username is required').min(5, 'Username must be at least 5 characters long'),
  password: yup.string().required('Password is required').min(6, 'Password must be at least 6 characters long'),
  birthdate: yup.date().nullable().required('Date of Birth is required').test('is-18-years-old', 'You must be at least 18 years old', function (value) {
    if (!value) {
      return false;
    }

    const today = new Date();
    const birthdate = new Date(value);
    const age = today.getFullYear() - birthdate.getFullYear();
    return age >= 18;
  }),
});

function validateField(fieldName) {
  try {
    validationSchema.validateAt(fieldName, formData);
    errors.value[fieldName] = '';
  } catch (error) {
    if (error instanceof yup.ValidationError) {
      errors.value[fieldName] = error.message;
    }
  }
}

async function submitForm() {
  try {
    await validationSchema.validate(formData, { abortEarly: false });
    alert('Registration successful!');
  } catch (error) {
    if (error instanceof yup.ValidationError) {
      errors.value = error.inner.reduce((acc, err) => {
        acc[err.path] = err.message;
        return acc;
      }, {});
    }
  }
}
</script>
