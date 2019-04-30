<template>
  <div class="row">
    <div class="column" v-for="col in 4">
      <quote v-for="quote in orderedQuotes[col - 1]" :content="quote"></quote>
    </div>
  </div>
</template>

<script>
import Quote from './Quote.vue'

export default {
  components: {
    Quote
  },
  props: {
    quotes: {
      type: Array
    }
  },
  data: function() {
    return {
      grid: []
    }
  },
  computed: {
    orderedQuotes() {
      let col = 0
      this.grid = [[], [], [], []]
      this.quotes.forEach((quote) => {
        this.grid[col].push(quote)
        col++
        if (col > 3) {
          col = 0
        }
      })
      return this.grid
    }
  }
}
</script>

<style scoped>
.row {
  display: flex;
  flex-wrap: wrap;
  padding: 0 16px;
  padding-bottom: 32px;
}

/* Create four equal columns that sits next to each other */
.column {
  flex: 25%;
  max-width: 25%;
  padding: 0 8px;
}

/* Responsive layout - makes a two column-layout instead of four columns */
@media screen and (max-width: 800px) {
  .column {
    flex: 50%;
    max-width: 50%;
  }
}

/* Responsive layout - makes the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .column {
    flex: 100%;
    max-width: 100%;
  }
}
</style>
