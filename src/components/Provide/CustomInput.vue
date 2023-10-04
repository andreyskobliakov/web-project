<template>
  <wrapper-custom-input :helperText="helperText" :error="error" :label="label">
    <input
      :type="type"
      :placeholder="placeholder"
      class="w-full px-4 py-2 rounded-md border-transparent placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
      @input="onSetValue"
      :value="value"
    />
  </wrapper-custom-input>
</template>

<script setup>
import { computed, inject, watch } from "vue";
import WrapperCustomInput from "../Provide/WrapperCustomInput.vue";
import { useField } from "../../composables/form";

defineEmits(['update:modelValue'])

const props = defineProps({
  placeholder: String,
  label: String,
  error: String,
  helperText: String,
  modelValue: String,
  type: {
    type: String,
    default: "text",
  },
  name: String,
})

const {value, onSetValue} = useField(props);

// const {errors, form} = inject("provideForm");


// const InnerValue = computed({
//   get() {
//     return form.value[props.name]
//   },
//   set(val) {
//     form.value[props.name] = val
//   }
// })

// const updateFormValue = (event) => {
//   InnerValue.value = event.target.value;
//   clearError();
// }

// const clearError = () => {
//   errors.value[props.name] = "";
// }

// watch(() => form.value[props.name], (newValue) => {
//   if (!newValue) {
//     errors.value[props.name] = `${props.label} is required`;
//   } else {
//     errors.value[props.name] = "";
//   }
// });
</script>
