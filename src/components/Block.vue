<template>
  <div class="box" v-if="showBox" @click="stopTimer"></div>
</template>
<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBox: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBox = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.showBox = false;
      this.$emit("stop", this.reactionTime);
    },
  },
};
</script>

<style>
.box {
  height: 40vh;
  width: 40%;
  border-radius: 10px;
  background-color: green;
  color: white;
  margin: 40px auto;
}
</style>
