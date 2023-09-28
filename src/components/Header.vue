<template>
    <header class="bg-gray-800 px-5 py-5">
      <div class="container flex items-center justify-between mx-0">
        <div class="flex items-center"> 
          <ThemeSwitcher/>
        </div>
        <div class="flex items-center justify-between"> 
          <input
            v-model="themeName"
            class="border rounded p-1"
            placeholder="Enter theme name"
          />
          <button
            class="btn btn-sm ml-2"
            @click="changeTheme(themeName)"
          >
            Change Theme
          </button>
        </div>
      </div>
    </header>
  </template>
  
  <script>
  import ThemeSwitcher from './ThemeSwitcher.vue';
  
  export default {
    components: {
      ThemeSwitcher,
    },
    data() {
      return {
        pageTitle: 'Заголовок вашей страницы',
        themeName: '', 
      };
    },
    methods: {
      changeTheme(theme) {
        if (theme) {
          document.documentElement.setAttribute("data-theme", theme);
        }
      },
    },
  };
  </script>
  