<template>
  <div class="progress">
    <div v-if="storage > 0" class="progress-bar" role="progressbar" :style="'width: ' + percentage + '%;'" :aria-valuenow="percentage" aria-valuemin="0" aria-valuemax="10">
      {{ storage }} / 10
    </div>
    <div v-else class="zero">
      Add a quote below to save it to your favorite quotes.
    </div>
  </div>
</template>

<script>
export default {
  props: {
    storage: {
      type: Number,
      required: true,
      validator: (v) => { return v <= 10 }
    }
  },
  computed: {
    percentage() {
      return this.storage * 10
    }
  }
}
</script>

<style scoped>
.progress {
  height: 24px;
  margin: 8px auto;
}
.progress-bar {
  background-color: #004085;
  font-weight: bold;
}
.zero {
  margin: 0 auto;
  color: gray;
  font-weight: normal;
  padding-top: 3px;
}
</style>
