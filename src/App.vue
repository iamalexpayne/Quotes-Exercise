<template>
	<div class="container">
		<header>
			<h2>Quotes Added</h2>
			<quote-storage-bar :storage="totalQuotes"></quote-storage-bar>
		</header>

		<quote-form @submittedNewQuote="addNewQuote($event)"></quote-form>
		<quote-grid :quotes="allQuotes"></quote-grid>

		<footer>
			<div class="alert alert-primary text-center" role="alert">To remove a quote, simply click on the quote.</div>
		</footer>
	</div>
</template>

<script>
import { quoteBus } from './main'
import QuoteStorageBar from './components/QuoteStorageBar.vue'
import QuoteForm from './components/QuoteForm.vue'
import QuoteGrid from './components/QuoteGrid.vue'

export default {
	components: {
		QuoteStorageBar,
		QuoteForm,
		QuoteGrid
	},
	data: function() {
		return {
			allQuotes: [],
		}
	},
	computed: {
		totalQuotes() {
			return this.allQuotes.length
		}
	},
	methods: {
		addNewQuote(quote) {
			if (this.totalQuotes === 10) {
				alert("Your quote storage is full!\n\nPlease delete some to add more.")
			} else {
				this.allQuotes.push(quote)
			}
		}
	},
	created() {
		quoteBus.$on('requestedQuoteDeletion', (quote) => {
			this.allQuotes = this.allQuotes.filter((q) => {
				return q !== quote
			})
		})
	}
}
</script>

<style scoped>
	.container {
		margin: 56px auto;
	}
</style>
