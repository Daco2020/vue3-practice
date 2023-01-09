<template>
	<div>
		<h2>보간법</h2>
		<p>{{ message }}</p>
		<p v-once>{{ message }}</p>
		<button v-on:click="message = message + '1'">버튼</button>
		<!-- v-once 는 업데이트 하지 않음 -->
		<hr />
		<br />
		<br />
		<h2>v-html을 사용한 경우</h2>
		<p>{{ rawHtml }}</p>
		<p v-html="rawHtml"></p>
		<!-- 사용자 올리는 게시물에 html을 사용하도록 하면 악성 스크립트를 삽입할 수 있으므로 주의 -->
		<br />
		<br />
		<h2>속성 바인딩</h2>
		<div v-bind:title="dynamicTitle">마우스를 올려보세요</div>
		<!-- 해당 div에 마우스를 올리면 title이 뜸 -->
		<input type="text" value="홍길동" v-bind:disabled="isInputDisabled" />
		<!-- v-bind:disabled 는 활성화를 의미함 -->
		<!-- v-bind는 자주사용하기 때문에 단축 속성명 ":" 만 쓸수도 있음 -->
		<input v-bind="attrs" />
		<!-- 바로 v-bind를 넣어 다중 속성을 넣을수도 있음 -->
		<br />
		<br />
		<br />
		<h2>js 문법도 사용가능</h2>
		{{ message.split('').reverse().join('') }}
		<br />
		{{ isInputDisabled ? '예' : '아니요' }}
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const message = ref('안녕!');
		const rawHtml = ref('<strong>스트롱</strong>');
		const dynamicTitle = ref('속성 바인딩이 뜰것이다');
		const isInputDisabled = ref(false);
		const attrs = ref({
			type: 'password',
			value: '123123',
			disabled: false,
		});

		return {
			message,
			rawHtml,
			dynamicTitle,
			isInputDisabled,
			attrs,
		};
	},
};
</script>

<style lang="scss" scoped></style>
