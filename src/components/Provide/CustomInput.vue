<template>
  <wrapper-custom-input :helperText="helperText" :error="error" :label="label">
    <input
      :type="type"
      :placeholder="placeholder"
      class="w-full px-4 py-2 rounded-md border-transparent placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
      @input="form[name] = $event.target.value"
      v-model="InnerValue"
    />
  </wrapper-custom-input>
</template>

<script setup>
import {computed, inject } from "vue";
import WrapperCustomInput from "../Provide/WrapperCustomInput.vue";

defineEmits(
    ['update:modelValue', ]
)

  const props = defineProps({
    placeholder: String,
    label: String,
    error: String,
    helperText: String,
    modelValue: String,
    type:  {
      type: String,
      default: "text"
    },
    name: String,
})

const InnerValue = computed({
  get(){
       return form.value[props.name]
  },

  set(val){
       form.value[props.name] = val
  }
})
const form = inject("formData");
</script>
<style scoped lang="scss">
</style>