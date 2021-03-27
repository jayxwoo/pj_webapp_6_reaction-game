<template>
  <div v-if="showBlock" class="block" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: null,
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      this.timer = clearInterval()
      this.$emit('end', this.reactionTime)
      console.log(this.reactionTime)
    },
  },
};
</script>

<style>
.block {
  width: 300px;
  height: 200px;
  margin: 2rem auto;
  background: var(--green);
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 1rem;
  color: white;
  font-weight: bold;
  font-size: 2rem;
  user-select: none;
}
</style>