<template>
  <header class="bg-white dark:bg-gray-800 shadow-md w-full relative z-50">
    <div class="container px-3 md:px-0 mx-auto flex items-center justify-between h-20 md:h-24">
      <div>
        <span class="text-purple-600 dark:text-white dark:bg-purple-600 text-l md:text-xl font-bold">reaction</span>
        <br>
        <span class="text-red-500 text-l dark:text-white dark:bg-red-500 md:text-xl font-bold">timer</span>
      </div>
      <div class="flex items-center space-x-4">
        <button class="bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded disabled:bg-purple-300 disabled:cursor-not-allowed" 
        @click="startGame"
        :disabled="isPlaying"
        >Play</button>

        <button class="w-10 h-10 p-2  rounded " @click="toggleDarkMode">
          <svg v-if="isDarkMode" fill="#FFFFFF" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M448 256c0-106-86-192-192-192V448c106 0 192-86 192-192zM0 256a256 256 0 1 1 512 0A256 256 0 1 1 0 256z"/></svg>
          <svg v-else fill="#000000" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M448 256c0-106-86-192-192-192V448c106 0 192-86 192-192zM0 256a256 256 0 1 1 512 0A256 256 0 1 1 0 256z"/></svg>
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  props: ["isPlaying"],
  data() {
    return {
      isDarkMode: false
    }
  },
  methods: {
    startGame() {
      this.$emit("start-game")
    },
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode
      document.documentElement.classList.toggle("dark")
    }
  }
}
</script>

<style>

</style>