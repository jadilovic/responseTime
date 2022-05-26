<template>
	<div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script>
export default {
	props: ['delay'],
	data() {
		return {
			showBlock: false,
			timer: null,
			reactionTime: 0,
		};
	},
	mounted() {
		console.log(this.delay);
		setTimeout(() => {
			this.showBlock = true;
			this.startTimer();
		}, this.delay);
	},
	methods: {
		startTimer() {
			this.timer = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},
		stopTimer() {
			clearInterval(this.timer);
			// console.log(this.reactionTime);
			this.$emit('end', this.reactionTime);
		},
	},
	updated() {
		console.log('updated');
	},
	unmounted() {
		console.log('unmounted');
	},
};
</script>

<style>
.block {
	width: 400px;
	height: 200px;
	border-radius: 20px;
	background: green;
	color: aliceblue;
	text-align: center;
	padding: 100px, 0;
	margin: 40px auto;
}
</style>
