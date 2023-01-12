<template>
	<div></div>
</template>

<script>
import { ref, watch, reactive } from 'vue';

export default {
	setup() {
		const x = ref(0);
		const y = ref(0);

		const obj = reactive({
			count: 0,
		});

		watch(
			() => x.value + y.value,
			(sum, oldValue) => {
				console.log('sum : ', sum);
				console.log('oldValue : ', oldValue);
			},
		);

		watch([x, y], ([newX, newY]) => {
			console.log(newX, newY);
		});

		console.log(typeof obj.count);

		watch(
			() => obj.count,
			(newValue, oldValue) => {
				console.log('newValue: ', newValue);
			},
		);

		watch(obj, (newValue, oldValue) => {
			console.log(newValue);
			console.log(oldValue);
		});

		const person = reactive({
			name: '다코',
			age: 30,
			hobby: '운동',
			obj: {
				count: 0,
			},
		});

		// 객체 전체를 보다가 변경이 있으면 반응
		watch(person, newValue => {
			console.log(newValue);
		});

		// person.obj 의 값이 변경될 때만 반응
		watch(
			() => person.obj,
			newValue => {
				console.log(newValue);
			},
		);
		return { x, y, obj, person };
	},
};
</script>

<style lang="scss" scoped></style>
