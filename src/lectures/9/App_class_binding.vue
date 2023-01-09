<template>
	<div>
		<div :class="{ active: isActive, 'text-danger': hasError }">
			텍스트 입니다.
		</div>
		<div :class="[isActive ? 'active' : 'etc-class', 'text-danger']">
			텍스트 입니다.
		</div>
		<button v-on:click="toggle">토글</button>
		<button v-on:click="hasError = !hasError">에러토글</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const isActive = ref(true);
		const hasError = ref(false);

		// /// 오브젝트로 클래스를 할당할 수도 있음
		// const classObject = reactive({
		// 	acitve: true,
		// 	'text-danger': true,
		// });
		// /// computed 오브젝트로 클래스를 할당할 수도 있음
		// const classObject = computed(() => {
		//   return {
		//     acitve: true,
		// 	'text-danger': true,
		//   }
		// })
		// /// + 배열과 삼항연산자로 클래스를 동적으로 여러개 할당할 수도 있음

		const toggle = () => {
			isActive.value = !isActive.value;
		};
		return { isActive, toggle, hasError };
	},
};
</script>

<style scoped>
.active {
	font-weight: 900;
}

.text-danger {
	color: red;
}
</style>
