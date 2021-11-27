<template>
  <div id="app">
    <AppHeader />
    <router-view />
    <div class="center">
      <button
        type="button"
        name="button"
        @click="play"
        :disabled="playState"
        class="item"
      >
        let's play
      </button>
      <block v-if="playState" :delay="delay" @end="endGame" class="item" />

      <result v-if="showResult" :score="score" class="item" />
    </div>

    <div class="" v-if="open">
      <AppFooter :footer="footer.ggg" :theme="theme" @open="openModel">
        <h1>I'm a slot footer</h1>
        <div>&copy; 2021 Eman Gamal.</div>
      </AppFooter>
    </div>
  </div>
</template>
<script>
import block from "@/components/global/block.vue";
import result from "@/components/global/result.vue";
import AppHeader from "@/components/global/navbar.vue";

export default {
  name: "App",
  data() {
    return {
      footer: {
        title: "uuu",
        ggg: "hello",
      },
      theme: "",
      openSecond: false,
      open: false,
      playState: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  components: {
    AppHeader,

    block,
    result,
  },
  methods: {
    play() {
      this.playState = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.showResult = true;
      this.playState = false;
    },
  },
};
</script>
<style media="screen" scoped>
.center {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.item {
  margin-top: 20px;
}
button {
  background-color: #35495e;

  border: none;
  color: #dddddd;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin-left: auto;
  margin-right: auto;
  border-radius: 8px;
}
</style>
