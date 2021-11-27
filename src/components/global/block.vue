<template lang="html">
  <div class="game" v-if="show" @click="stopTimer">
    <div class="child">
      <h4>this is the game</h4>
    </div>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      show: false,
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
    setTimeout(() => {
      this.show = true;
      this.startTimer();
    }, this.delay);
  },
};
</script>

<style lang="css" scoped>
.game {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 70%;

  height: 500px;
  background-color: #41b883;
  border-radius: 20px;
  text-align: center;
}
.child {
  width: 500px;
  height: 50px;
}
</style>
