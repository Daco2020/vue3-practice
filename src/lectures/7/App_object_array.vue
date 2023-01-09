<template>
	<div></div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
	setup() {
		// ref -> Object
		// 객체에서 ref 를 사용할 때는 value가 언래핑되므로 붙이지 않는다.
		const count = ref(0);
		const state = reactive({
			count,
		});
		count.value++;

		console.log('count: ', count); // 1
		console.log('state.count: ', state.count); // 1
		console.log('state.count.value: ', state.count.value); // undefined

		// ref -> Array
		// 배열에서 ref 를 사용할 때는 value를 붙여서 가져온다.
		const message = ref('hello');
		const arr = reactive([message]);
		console.log('arr[0]: ', arr[0].value);
		return {};
	},
};
</script>

<style lang="scss" scoped></style>
