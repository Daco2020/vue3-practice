<template>
	<div>
		<span>{{ count }}</span>
		<button @click="count++">카운트 증가</button>
	</div>
</template>

<script>
import { ref } from 'vue';
export default {
	setup() {
		const count = ref(0);
		return {
			count,
		};
	},
};
</script>

<style lang="scss" scoped></style>
