<template>
	<!-- memo 배열 안에 있는 요소만 반응한다 -->
	<!-- 성능최적화에 사용 -->
	<div v-memo="[subscribers]">
		<p>a : {{ subscribers }}</p>
		<p>b : {{ views }}</p>
		<p>c : {{ likes }}</p>
	</div>
	<!-- v-on: -> @ 로 단축할 수 있음 -->
	<button @click="subscribers++">sub++</button>
	<button @click="views++">view++</button>
	<button @click="likes++">like++</button>
	<div>
		<p>a : {{ subscribers }}</p>
		<p>b : {{ views }}</p>
		<p>c : {{ likes }}</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const subscribers = ref(4000);
		const views = ref(400);
		const likes = ref(20);
		return { subscribers, views, likes };
	},
};
</script>

<style lang="scss" scoped></style>
