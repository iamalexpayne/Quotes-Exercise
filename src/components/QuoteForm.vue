<template>
  <form @submit.prevent="addNewQuote">
    <div class="form-group">
      <label for="quoteTextarea">Quote</label>
      <textarea v-model="quote" class="form-control" id="quoteTextarea" rows="3"></textarea>
    </div>
    <div class="col text-center">
      <button class="btn btn-primary">Add Quote</button>
    </div>
  </form>
</template>

<script>
export default {
  data: function() {
    return {
      quote: ''
    }
  },
  methods: {
    addNewQuote() {
      this.$emit('submittedNewQuote', this.quote)
      this.quote = ''
    }
  }
}
</script>

<style scoped>
form {
  max-width: 560px;
  margin: 0 auto;
  padding: 16px 0;
}
label {
  font-weight: bold;
}
textarea {
  resize: none;
  font-size: 2em;
  font-family: 'Arizonia', cursive;
}
button {
  background-color: #004085;
}
</style>
