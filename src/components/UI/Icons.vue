<template>
    <i class="material-icons">{{ iconName }}</i>
  </template>
  
  <script>
  export default {
    props: {
      iconName: {
        type: String,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  
  </style>
  