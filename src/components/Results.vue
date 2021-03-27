<template>
  <p class="results">
    Your Reaction Time : <span class="results-score">{{ score }}</span
    >ms
  </p>
  <p class="results-rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja Reflexes!!"
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes!"
    } else {
      this.rank = "Snail Reflexs.."
    }
  },
};
</script>

<style>
.results {
  margin-top: 2rem;
  font-size: 1rem;
}
.results-score {
  font-weight: bold;
  color: var(--green);
}
.results-rank {
    font-size: 1.5rem;
    color: var(--green);
    text-transform: uppercase;
    font-weight: bold;
    margin-top: 1rem;
}
</style>