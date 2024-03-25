<template>
  <p>Reaction time - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if(this.score<250) {
      this.rank = "ninja fingers"
    } else if(this.score < 400) {
      this.rank = "Rapid Reflexes"
    } else {
      this.rank = "snail pace..."
    }
  }
}
</script>

<style>
.rank {
  font-weight: bold;
  font-size: 1.4rem;
  color: #0faf87;
}
</style>