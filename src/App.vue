<template>
  <Header @start-game="startGame" :isPlaying="isPlaying" />
  <div class="flex-grow  dark:bg-gray-700" :class="{
    'bg-yellow-50': !isPlaying,
    'bg-green-50': isPlaying
    }">
    <div class="h-full px-3 md:px-0 md:container md:mx-auto w-100 py-3 relative flex justify-center " ref="playGround">
      <Block v-if="isPlaying" :delay="delay" :posX="posX" :posY="posY" @end-game="endGame" />
      <Result v-else-if="!isPlaying && point !== null" :point="point" :points="points" @start-game="startGame"/>
      <Start v-else />
    </div>
  </div>
  <div class="px-3 py-1 bg-white dark:bg-gray-800 border-t-2 border-purple-200 border-dotted text-center dark:border-gray-700">
      <span class="text-xs text-gray-600 dark:text-gray-400">Created by <a href="https://mehmetsahin.dev" target="_blank">Mehmet Şahin</a></span>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Block from './components/Block.vue'
import Result from './components/Result.vue'
import Start from './components/Start.vue'

export default {
  data() {
    return {
      isPlaying: false,
      delay: null,
      posX: null,
      posY: null,
      point: null,
      points: []
    }
  },
  components: { Header, Block, Result, Start },
  methods: {
    startGame() {
      let playGroundHeight = this.$refs.playGround.clientHeight
      let playGroundWidth = this.$refs.playGround.clientWidth
      let blockWidth = 128;
      let blockHeight = 128;

      this.point = null

      this.delay = 2000 + Math.random() * 5000

      this.posX = Math.floor(Math.random() * (playGroundWidth - blockWidth))
      this.posY = Math.floor(Math.random() * (playGroundHeight - blockHeight))

      console.log("pgW", playGroundWidth);
      console.log("pgH", playGroundHeight);

      console.log("posX", this.posX);
      console.log("posY", this.posY);

      //if (this.posX > (playGroundWidth - blockWidth)) this.posX = playGroundWidth - blockWidth;
      //if (this.posY > (playGroundHeight - blockHeight)) this.posY = playGroundHeight - blockHeight;

      this.isPlaying = true;
    },
    endGame(point) {
      this.posX = null
      this.posY = null
      this.point = point
      this.points.unshift(point)
      this.isPlaying = false
    }
  },
}
</script>

<style>
  #app {
    @apply flex flex-col h-screen max-h-screen
  }
  body {
    @apply h-screen
  }
</style>