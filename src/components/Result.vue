<template>
  <p>Reaction time - {{ score }} ms</p>
  <h3>{{ rank }}</h3>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: "",
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja Fingers";
    } else if (this.score < 400) {
      this.rank = "Quick Reflexes";
    } else {
      this.rank = "...Snail Pace";
    }
  },
};
</script>

<style>
h3 {
  color: green;
}
</style>
