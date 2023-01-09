<template>
	<div>
		<h2>반응형 메시지</h2>
		<p>{{ reactiveMessage }}</p>
		<button v-on:click="addReactiveMessage">반응형 메시지 더하기</button>

		<h2>일반 메시지</h2>
		<p>{{ normalMessage }}</p>
		<button v-on:click="addNormalMessage">일반 메시지 더하기</button>
	</div>
</template>

<script>
import { isRef, ref, onMounted, onBeforeMount } from 'vue';

export default {
	setup() {
		console.log('setup');
		const reactiveMessage = ref('Hello Message');
		const addReactiveMessage = () => {
			reactiveMessage.value = reactiveMessage.value + '!';
		};
		// 반응형 API는 유저 액션에 의해 수정되는 경우 사용한다.
		// isRef 는 반응형 데이터인지 확인해주는 메서드이다.
		console.log('reactiveMessage', isRef(reactiveMessage)); // true

		let normalMessage = 'Hello Normal Message';
		const addNormalMessage = () => {
			normalMessage = normalMessage + '!'; // 실제 동작하지 않는다.
		};
		console.log('reactiveMessage', isRef(normalMessage)); // false

		/// 라이프사이클 훅: 라이프사이클 단계에서 실행되는 함수, e.g. 마운트 전/후
		onBeforeMount(() => {
			console.log('onBeforeMount');
		});
		onMounted(() => {
			console.log('onMounted');
		});

		return {
			reactiveMessage,
			normalMessage,
			addReactiveMessage,
			addNormalMessage,
		};
	},
};
</script>

<style lang="scss" scoped></style>
