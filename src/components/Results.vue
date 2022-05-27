<template>
	<h1>Your score is {{ score }}</h1>
	<h3>{{ rank }}</h3>
</template>

<script>
export default {
	props: ['score'],
	data() {
		return {
			rank: null,
		};
	},
	mounted() {
		if (this.score < 200) {
			this.rank = 'Ninja fingers';
		} else if (this.score < 400) {
			this.rank = 'Very fast';
		} else {
			this.rank = 'Snail paste...';
		}
	},
};
</script>

<style>
h3 {
	color: aqua;
}
</style>
