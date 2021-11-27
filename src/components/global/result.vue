<template lang="html">
  <div class="container">
    <h3>the score is {{ score }}</h3>
    <p>the rank is {{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return { rank: null };
  },
  mounted() {
    if (this.score < 260) {
      this.rank = "ninga finger";
    } else if (this.score < 400) {
      this.rank = "not bad";
    } else {
      this.rank = "snail finger";
    }
  },
};
</script>

<style lang="css" scoped>
.container {
  text-align: center;
}
</style>
