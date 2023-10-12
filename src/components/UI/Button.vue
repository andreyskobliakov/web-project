// Button.vue

<template>
  <button
    :class="[buttonClass, buttonColorClass, buttonStyleClass, buttonSizeClass, buttonDisabledClass, buttonSquareClass, buttonFabClass]"
    @click="handleClick"
    :disabled="disabled"
  >
  <slot name="icon"></slot>
    <slot></slot>
    {{ text }}
  </button>
</template>

<script>
import { defineProps, defineEmits } from 'vue';

export default {
  props: {
    text: String,
    variant: {
      type: String,
      default: 'primary',
    },
    color: String,
    outlined: Boolean,
    contained: Boolean,
    size: String,
    disabled: Boolean,
    square: Boolean,
    fab: Boolean,
  },
  setup(props) {
    const { text, variant, color, outlined, contained, size, disabled, square, fab } = props;
    const emit = defineEmits(this);

    const buttonClass = `px-4 py-2 rounded focus:outline-none ${
      variant === 'primary' ? 'bg-blue-500 text-white' :
      variant === 'secondary' ? 'bg-gray-500 text-white' :
      'bg-gray-300 text-gray-800'
    }`;

    const buttonColorClass = color ? `text-${color}-500` : '';
    
    const buttonStyleClass = outlined
      ? 'border border-solid border-blue-500'
      : contained
      ? 'bg-blue-500 hover:bg-blue-600'
      : '';

    const buttonSizeClass = size === 'small' ? 'text-sm' : size === 'large' ? 'text-lg' : '';
    const buttonDisabledClass = disabled ? 'opacity-50 cursor-not-allowed' : '';

    const buttonSquareClass = square ? 'rounded-full' : '';
    const buttonFabClass = fab ? 'rounded-full w-12 h-12' : '';

    const handleClick = () => {
      emit('click');
    };

    return {
      text,
      buttonClass,
      buttonColorClass,
      buttonStyleClass,
      buttonSizeClass,
      buttonDisabledClass,
      buttonSquareClass,
      buttonFabClass,
      handleClick,
    };
  },
};
</script>

<style scoped>
</style>
