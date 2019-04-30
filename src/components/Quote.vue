<template>
	<div
		title="click to delete this quote"
		@click="requestDeletion">
			{{ content }}
	</div>
</template>

<script>
import { quoteBus } from '../main'

export default {
	props: {
		content: String
	},
	methods: {
		requestDeletion() {
			quoteBus.$emit('requestedQuoteDeletion', this.content)
		}
	}
}
</script>

<style scoped>
div {
	padding: 16px;
	margin-top: 16px;
	vertical-align: middle;
	border-radius: 16px;
	box-shadow: 0 4px 7px lightgray;
	text-align: center;
	font-size: 2em;
	font-family: 'Arizonia', cursive;
	word-wrap: break-word;
	transition: all .3s ease-in-out;
}
div:hover {
	background-color: lightpink;
	cursor: pointer;
}
</style>
