<template>
  <div class="mt-10 w-full flex flex-col items-center">
    <div class="flex flex-col justify-center items-center">
        <span class=" text-2xl font-thin dark:text-gray-300">Your Time</span>
        <span class="text-4xl font-bold mt-3 text-purple-600 dark:text-white">{{ point }} ms</span>
    </div>
    <div class="text-center mt-10">
        <button class="bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded disabled:bg-purple-300 disabled:cursor-not-allowed" 
        @click="startGame"
        >Play Again</button>
    </div>
    <div class="mt-10 border rounded text-center bg-white w-full md:w-2/4" v-if="points.length">
        <div class="bg-gray-200 py-3">Latest Times</div>
        <div class=" overflow-y-auto max-h-56 ">
            <div v-for="(pointText, index) in points" :key="index" class="mt-334234">
                <hr class="mb-3">
                <span class="mb-3 block">{{ pointText }} ms</span>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    props: ["point", "points"],
    methods: {
        startGame() {
        this.$emit("start-game")
        }
    }
}
</script>

<style>

</style>