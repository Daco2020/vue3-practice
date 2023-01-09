<template>
	<div>
		<h2 v-if="visible">visible vue</h2>
		<h2 v-else>false 입니다.</h2>
		<button v-on:click="visible = !visible">visible_toggle</button>

		<br />
		<hr />
		<br />

		<button v-on:click="type = 'A'">A</button>
		<button v-on:click="type = 'B'">B</button>
		<button v-on:click="type = 'C'">C</button>
		<button v-on:click="type = 'D'">D</button>

		<h2 v-if="type === 'A'">A랑께</h2>
		<h2 v-else-if="type === 'B'">B랑께</h2>
		<h2 v-else-if="type === 'C'">C랑께</h2>
		<h2 v-else>ABC 아니여</h2>

		<br />
		<hr />
		<br />

		<template v-if="visible">
			<h1>template h1</h1>
			<p>p1</p>
			<p>p2</p>
		</template>

		<br />
		<hr />
		<br />

		<h1 v-show="ok">v-show 입니다</h1>
		<button v-on:click="ok = !ok">v-show 토글</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const visible = ref(false);
		const type = ref('A');
		const ok = ref(true);
		return { visible, type, ok };
	},
};
</script>

<style lang="scss" scoped></style>
