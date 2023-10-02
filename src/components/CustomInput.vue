<template>
  <wrapper-custom-input
    :helperText="helperText"
    :error="error"
    :label="label"
    :formData="formData"
  >
    <input
      :type="type"
      :placeholder="placeholder"
      class="peer block min-h-[auto] w-full rounded ring-1 bg-transparent px-3 py"
      :value="formData.Login"
      @input="$emit('update:modelValue', $event)"
    />
  </wrapper-custom-input>
</template>

<script setup>
import { inject } from "vue";

const formData = inject("formData", null);

const { placeholder, label, error, helperText, modelValue, type } =
  defineProps({
    placeholder: String,
    label: String,
    error: String,
    helperText: String,
    modelValue: String,
    type: {
      type: String,
      default: "text",
    },
  });
</script>
