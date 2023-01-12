<template>
	<div>
		<p>{{ message }}</p>
		<p>{{ reverseMessage }}</p>
	</div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const message = ref('hello daco');
		const reverseMessage = ref('');

		const reverseFunction = () => {
			console.log('최초실행');
			reverseMessage.value = message.value.split('').reverse().join('');
		};
		watch(message, reverseFunction);
		reverseFunction();
		return { message, reverseMessage };
	},
};
</script>

<style lang="scss" scoped></style>
