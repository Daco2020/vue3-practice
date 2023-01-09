<template>
	<div></div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		const state = reactive({ count: 0 });
		// reactive는 원시값을 사용하면 반응형으로 사용할 수 없음.
		// 객체에 넣어서 사용해야하는데 이를 쉽게 하는 것이 ref 임.

		return {
			state,
		};
	},
};
</script>

<style lang="scss" scoped></style>
