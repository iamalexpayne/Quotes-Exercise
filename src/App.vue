<template>
	<div class="container">
		<header>
			<h2>Quotes Added</h2>
			<quote-storage></quote-storage>
		</header>

		<quote-form></quote-form>
		<quote-grid>
			<quote v-for="quote in allQuotes">{{ quote }}</quote>
		</quote-grid>

		<footer>
			<div class="alert alert-primary text-center" role="alert">To remove a quote, simply click on the quote.</div>
		</footer>
	</div>
</template>

<script>
	export default {

	}
</script>

<style scoped>
	.container {
		margin: 56px auto;
	}
</style>
