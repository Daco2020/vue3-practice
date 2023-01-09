<template>
	<button @click="count++">{{ count }}</button>
</template>

<script>
import { ref } from 'vue';

export default {
	props: {
		title: String,
	},
	setup(props, { attrs, slots, emit, expose }) {
		// 두번째 인수는 context
		console.log(props.title);
		const count = ref(0);

		// 속성($attrs와 동일한 비반응형 객체)
		console.log(attrs);

		// 슬롯($slots에 해당하는 비반응성 개체)
		console.log(slots);

		// 이벤트 발생($emit에 해당하는 함수)
		console.log(emit);

		// Public한 속성, 함수를 외부에 노출시에 사용
		console.log(expose);

		// 템플릿 및 기타 Options API hook에 노출
		return {
			count,
		};
	},
	mounted() {
		console.log(this.count); // this 로 사용 가능, 근데 잘 사용하지 않음
	},
};
</script>
