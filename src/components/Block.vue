<template>
  <div v-if="showBlock" @click="endGame" class="bg-red-600 w-32 h-32 rounded-lg absolute text-white flex items-center justify-center"
  :style="{
    top: posY + 'px',
    left: posX + 'px'
  }"
  > click me pls</div>
  <div v-else class="w-100 h-full flex flex-col items-center">
    <span class=" block mt-32 text-gray-300 text-5xl font-bold ">Comiiiiing...</span>
  </div>
</template>

<script>
export default {
    props: ["delay", "posX", "posY"],
    data() {
        return {
            showBlock: false,
            timer: null,
            point: null
        }
    },
    methods: {
        endGame() {
            clearInterval(this.timer);
            this.$emit("end-game", this.point)
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.timer = setInterval(() => {
                this.point += 10;
            }, 10)
        }, this.delay);
    }
}
</script>

<style>

</style>