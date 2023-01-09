<template>
	<div></div>
</template>

<script>
import { reactive, toRefs, toRef } from 'vue';

export default {
	setup() {
		const book = reactive({
			author: 'Vue Team',
			year: '2020',
			title: 'Vue 3 Guide',
			description: '당신은 지금 바로 이 책을 읽습니다  ;)',
			price: '무료',
		});

		let { author, title } = toRefs(book); // toRefs을 쓰지 않으면 구조분해 할당시 반응형을 잃게됨
		let price = toRef(book, 'price'); // toRefs을 쓰지 않으면 구조분해 할당시 반응형을 잃게됨

		title.value = 'Vue 3 상세 Guide'; // title 이 ref 이므로 .value 를 사용해야 합니다.
		author.value = '뀽';
		price.value = '끵';
		console.log(book.title); // 'Vue 3 상세 Guide'
		console.log(book.author); // '뀽'
		console.log(book.price); // '끵'
		return {};
	},
};
</script>

<style lang="scss" scoped></style>
