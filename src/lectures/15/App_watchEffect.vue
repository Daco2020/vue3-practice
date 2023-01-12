<template>
	<div>
		<form @submit.prevent>
			<input v-model.lazy="title" type="text" placeholder="Title" />
			<br />
			<textarea v-model.lazy="contents" placeholder="Contents"></textarea>
			<hr />
			<button @click="save(title, contents)">저장</button>
		</form>
	</div>
</template>

<script>
import { ref, watchEffect } from 'vue';

export default {
	setup() {
		const title = ref('');
		const contents = ref('');

		const save = (title, contents) => {
			console.log(`저장 ${title}, ${contents}`);
		};
		watchEffect(() => {
			console.log('watchEffect');
			save(title.value, contents.value);
		});
		return { title, contents, save };
	},
};
</script>

<style lang="scss" scoped></style>

<!-- ## 
	
`watch` vs `watchEffect`

`watch`와 `watchEffect` 둘 다 관련 작업(api call, push route 등)을 반응적으로 수행할 수 있게 해줍니다. 
하지만 주요한 차이점은 관련된 반응형 데이터를 추적하는 방식입니다.

watch 는 명시적 watchEffect는 덜 명시적
둘다 즉시 동작시킬수 있음 watchEffect는 자동

-->
