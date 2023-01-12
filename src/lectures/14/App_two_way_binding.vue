<template>
	<!-- v-model 을 이용하여 양방햔 바인딩을 구현할 수 있다 -->
	<div>
		<h2>input Value</h2>
		<!-- <input type="text" v-model="inputValue" /> -->
		<!-- 입력이 완료 된 후 동기화 -->
		<!-- <input type="text" v-model.lazy="inputValue" /> -->
		<!-- 숫자를 입력하면 number 로 형 변환, 숫자 연산에 유용 -->
		<!-- <input type="text" v-model.number="inputValue" /> -->
		<!-- 빈 공백 없애기 -->
		<input type="text" v-model.trim="inputValue" />
		<div>{{ inputValue }}</div>
		<div>{{ typeof inputValue }}</div>

		<h2>textarea value</h2>
		<textarea v-model="textareaValue"></textarea>
		<div>{{ textareaValue }}</div>

		<h2>checkbox value</h2>
		<label for="checkbox">{{ checkboxValue }}</label>
		<input
			type="checkbox"
			id="checkbox"
			v-model="checkboxValue"
			true-value="꿍꿍이"
			false-value="낑낑이"
		/>
		<h3>checkbox values</h3>
		<label>
			<input type="checkbox" value="html" v-model="checkboxValues" />
			html
		</label>
		<label>
			<input type="checkbox" value="css" v-model="checkboxValues" />
			css
		</label>
		<label>
			<input type="checkbox" value="javascript" v-model="checkboxValues" />
			javascript
		</label>
		<div>{{ checkboxValues }}</div>

		<h2>radio value</h2>
		<label>
			<input type="radio" name="type" value="O" v-model="radioValue" />
			O형
		</label>
		<label>
			<input type="radio" name="type" value="A" v-model="radioValue" />
			A형
		</label>
		<div>
			{{ radioValue }}
		</div>

		<h2>select value</h2>
		<select v-model="selectValue">
			<option value="html">HTML 수업</option>
			<option value="css">CSS 수업</option>
			<option value="javascript">JavaScript 수업</option>
		</select>
		<div>{{ selectValue }}</div>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const inputValue = ref(null);
		const textareaValue = ref(null);
		const checkboxValue = ref('꿍꿍이');
		const checkboxValues = ref([]);
		const radioValue = ref('O');
		const selectValue = ref('html');
		return {
			inputValue,
			textareaValue,
			checkboxValue,
			checkboxValues,
			radioValue,
			selectValue,
		};
	},
};
</script>

<style lang="scss" scoped></style>
