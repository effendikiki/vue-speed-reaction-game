<template>
  <br />
  <h4>
    {{ resultMessage }} <br />
    Your reaction time is <b>{{ reactionTime }}</b> miliseconds
  </h4>
</template>

<script>
export default {
  name: "Result",
  props: ["reactionTime"],
  data() {
    return {
      resultMessage: null,
    };
  },
  mounted() {
    if (this.reactionTime < 400) {
      this.resultMessage = "Pretty fast aren't you? 😉";
    } else if (this.reactionTime < 650) {
      this.resultMessage = "Not Bad!";
    } else {
      this.resultMessage = "Come on you gotta try faster! 😂";
    }
  },
};
</script>

<style></style>
