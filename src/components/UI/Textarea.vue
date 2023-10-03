<template>
  <textarea :value="value" @input="updateValue" :placeholder="placeholder" class="textarea textarea-bordered "></textarea>
</template>

<script>
export default {
  props: {
    value: String,
    placeholder: String,
  },
  methods: {
    updateValue(event) {
      this.$emit("update:value", event.target.value);
    },
  },
};
</script>

<style scoped>
.textarea {
  @apply px-3 py-2 text-base border rounded-lg focus:outline-none focus:border-stone-950 transition duration-300 ease-in-out;
}
</style>
