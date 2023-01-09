<template>
	<div></div>
</template>

<script>
import { reactive, readonly } from 'vue';

export default {
	setup() {
		const original = reactive({ count: 0 });

		const copy = readonly(original);

		// 원본이 변이되면 복사본에 의존하는 watch 도 트리거될 것 입니다.
		original.count++;
		console.log(original.count);

		// 복사본을 변이하려고 하면 경고와 함께 실패할 것 입니다.
		copy.count--; // warning: "Set operation on key 'count' failed: target is readonly."
		console.log(copy.count);
		return {};
	},
};
</script>

<style lang="scss" scoped></style>
