<template>
	<div>
		<!-- 안녕하세요 -->
		<p>{{ msg }}</p>
		<!-- 안녕하세요 -->
		<p v-text="msg"></p>
		<!-- **뀨!** -->
		<p v-html="htmlStr"></p>
		<!-- <strong>뀨!</strong> -->
		<p v-text="htmlStr"></p>
		<!-- 표현식을 허용하지 않음 그대로 보여줌 -->
		<!-- {{ msg 안녕하세요}} -->
		<p v-pre>{{ msg 안녕하세요}}</p>
		<!-- 안녕하세요 -->
		<!-- 이후 변경되지 않음. 업데이트 성능최적화 -->
		<p v-once>{{ msg }}</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const msg = ref('안녕하세요');
		const htmlStr = ref('<strong>뀨!</strong>');
		return { msg, htmlStr };
	},
};
</script>

<style lang="scss" scoped></style>

<!-- 

// v-cloak 컴파일 되기 전까지 v-cloak 선택자를 지정해 스타일을 바꿔줄 수 있다.
// 안보이게 하거나 로딩중을 표현할 수 있다.

<style>
[v-cloak] {
	display: none;
}
</style>

<template>
<div v-cloak>
  {{ message }}
</div> 
</template>

-->
