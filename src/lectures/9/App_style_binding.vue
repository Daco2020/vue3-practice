<template>
	<div>
		<button v-on:click="fontSize++">+</button>
		<button v-on:click="fontSize--">-</button>
		<div :style="styleObject">
			Lorem ipsum dolor sit, amet consectetur adipisicing elit. Mollitia omnis
			sequi ex ab maxime. Nihil tenetur eaque ipsa pariatur quis suscipit
			blanditiis deserunt sint quasi totam impedit ex, voluptatem quod.
		</div>
	</div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
	setup() {
		const fontSize = ref(13);
		/// reactive 사용하는 방법
		// const styleObject = reactive({
		// 	color: 'red',
		// 	fontSize: fontSize.value + 'px',
		// });
		/// computed 사용하는 방법
		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});
		return { styleObject, fontSize };
	},
};
</script>

<style lang="scss" scoped></style>
