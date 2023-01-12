<template>
	<input type="text" v-model="message" />
	<div>{{ message }}</div>
	<div>new : {{ a }}</div>
	<div>old : {{ b }}</div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const message = ref('');
		const a = ref('');
		const b = ref('');

		// 새로운 값과 기존 값을 함께 가지고 있음
		watch(message, (newValue, oldValue) => {
			// DOM~

			// API~
			// state 변경
			console.log(newValue);
			console.log(oldValue);
			a.value = newValue;
			b.value = oldValue;
		});
		return { message, a, b };
	},
};
</script>

<style lang="scss" scoped></style>
