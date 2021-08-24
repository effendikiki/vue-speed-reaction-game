<template>
  <div v-if="showBox" class="container" align="center">
    <div class="box" @click="stopTimer">Click Me!!</div>
  </div>
</template>

<script>
export default {
  name: "TargetBox",
  props: ["delay"],
  data() {
    return {
      showBox: false,
      timer: null,
      reactionTime: 0,
    };
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
  mounted() {
    console.log("mounted");
    setTimeout(() => {
      this.showBox = true;
      this.startTimer();
    }, this.delay);
  },
};
</script>

<style scoped>
.container {
  margin-top: 10%;
}
.box {
  padding: 20px;
  width: 40%;
  height: 200px;
  border-radius: 10px;
  box-shadow: 0 2px 15px lightblue;
  display: grid;
  place-items: center;
}
</style>
