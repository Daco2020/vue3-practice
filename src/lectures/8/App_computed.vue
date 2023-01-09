<template>
	<div>
		<h2>{{ teacher.name }}</h2>
		<h3>강의가 있나요?</h3>
		<!-- <p>{{ teacher.lectures.length > 0 ? '있음' : '없음' }}</p> -->
		<!-- 이렇게 쓰면 가독성이 떨어지고 읽기 어려우므로  -->
		<p>{{ hasLecture }}</p>
		<p>{{ hasLecture }}</p>
		<p>{{ hasLecture }}</p>
		<p>{{ existLecture() }}</p>
		<p>{{ existLecture() }}</p>
		<p>{{ existLecture() }}</p>
		<!-- hasLecture는 1번, existLecture는 3번 실행됨  -->
	</div>
</template>

<script>
import { reactive, computed } from 'vue';

export default {
	setup() {
		const teacher = reactive({
			name: '다코',
			lectures: ['a', 'b', 'c'],
		});

		// 템플릿으로 전달하기 전에 계산 함수를 변수에 할당하여 반환할 수 있음
		// 반응형 데이터가 변경되기 전까지는 캐싱하여 반환함
		const hasLecture = computed(() => {
			console.log('computed');
			return teacher.lectures.length > 0 ? '뀽' : '끵';
		});
		// 기본적으로 get 만 되나 set을 추가하여 쓰기도 구현할 수 있음(아래 예시)
		// 대신 콜백함수가 아닌 객체 매개변수로 정의한다. (콜백: () => {})
		// const fullName = computed({
		//   get() {
		//     return firstName.value + ' ' + lastName.value;
		//   },
		//   set(newValue) {
		//     [firstName.value, lastName.value] = newValue.split(' ');
		//   },
		// });
		// fullName.value = '안녕 하세요'; // set 동작함

		/// 함수 자체를 반환할 수 있음
		// 하지만 computed 가 성능면에서 우위. 왜냐하면 결과를 캐싱하기 때문임
		const existLecture = () => {
			console.log('method');
			return teacher.lectures.length > 0 ? '뀽' : '끵';
		};

		return { teacher, hasLecture, existLecture };
	},
};
</script>

<style lang="scss" scoped></style>
