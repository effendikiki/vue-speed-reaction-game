<template>
  <main class="container" align="center">
    <h1>Speed Reaction Game</h1>
    <p>
      Let's see how quick your reaction is! <br />
      Click start and wait for the target to come out, then click it as fast as
      you can!
    </p>
    <div>
      <button :disabled="isPlaying" class="button-outline" @click="start">
        Start
      </button>
      <button
        :disabled="!isPlaying"
        class="button-clear"
        @click="reset"
        style="margin-left: 5px"
      >
        Reset
      </button>
    </div>
    <Result v-if="showResult" :reactionTime="reactionTime" />
    <TargetBox v-if="isPlaying" :delay="delay" @end="endGame" />
  </main>
</template>

<script>
import TargetBox from "./components/TargetBox.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: { TargetBox, Result },
  data() {
    return {
      isPlaying: false,
      showResult: false,
      delay: null,
      reactionTime: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 3000;
      this.isPlaying = true;
    },
    endGame(reactionTime) {
      this.reactionTime = reactionTime;
      this.showResult = true;
    },
    reset() {
      this.isPlaying = false;
      this.showResult = false;
    },
  },
};
</script>

<style scoped>
* {
  transition: all 0.3s;
}
main {
  margin-top: 10%;
  padding-bottom: 50px;
}
</style>
