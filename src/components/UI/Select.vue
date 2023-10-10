<template>
  <div>
    <select v-model="selectedValue" @input="updateValue" class="select select-bordered w-full max-w-xs">
      <option disabled selected>{{ placeholder }}</option>
      <option v-for="option in options" :key="option" :value="option">{{ option }}</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    value: String, 
    placeholder: String,
    options: Array,
  },
  data() {
    return {
      selectedValue: this.value, 
    };
  },
  watch: {
    value(newValue) {
      this.selectedValue = newValue; 
    },
  },
  methods: {
    updateValue() {
      this.$emit("update:value", this.selectedValue); 
    },
  },
};
</script>

<style scoped>
.select {
  @apply px-3 py-2 text-base border rounded-lg focus:outline-none focus:border-stone-950 transition duration-300 ease-in-out;
}
.select::placeholder {
  @apply text-gray-400;
}
</style>
