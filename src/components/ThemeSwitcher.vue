<template>
  <div class="flex justify-between">
    <div>
      <button
        class="btn btn-sm ml-5 mb-1"
        v-for="theme in themes"
        :key="theme"
        @click="changeTheme(theme)"
      >
        {{ theme }} Theme
      </button>
    </div>

    
  </div>
</template>

<script>
export default {
  data() {
    return {
      themes: ["light", "dark", "retro", "coffee", "aqua", "dracula"],
      selectedTheme: "",
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
