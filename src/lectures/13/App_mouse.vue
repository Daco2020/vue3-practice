<template>
	<div>
		<div id="modifiers">
			<!-- capture 는 나 먼저 실행할거야 라는 뜻 -->
			<div @click.capture="clickDiv">
				div
				<!-- self는 클릭 요소가 나 일때만 이벤트 실행 -->
				<p @click.self="clickP">
					p
					<!-- stop은 다른 이벤트와 중첩되지 않고 자신만 실행 -->
					<span @click.stop="clickSpan"> span </span>

					<!-- once는 한번만 실행함 -->
					<span @click.once="clickSpan"> span </span>
					<!-- prevent > 기본기능 막기 / stop > 이벤트 중첩 막기 -->
					<!-- 둘을 체이닝하여 사용할 수 있음 -->
					<a href="https://naver.com" @click.prevent.stop="clickA">a</a>
				</p>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	setup() {
		const clickDiv = () => {
			console.log('Div');
			// location.href = 'https://naver.com';
		};
		const clickP = () => {
			console.log('P');
		};
		const clickSpan = () => {
			console.log('Span');
			// alert('좋아요');
		};
		const clickA = e => {
			e.preventDefault(); // 여기에 쓸수도 있고 template에서 쓸수도 있음
			alert('A태그');
		};
		return {
			clickDiv,
			clickP,
			clickSpan,
			clickA,
		};
	},
};
</script>

<style scoped>
#modifiers div,
#modifiers p,
#modifiers span {
	padding: 40px;
}
#modifiers div {
	background-color: tomato;
}
#modifiers p {
	background-color: aquamarine;
}
#modifiers span {
	background-color: bisque;
	display: block;
}
</style>

<!--  아래처럼 하면 div, p, span 의 이벤트가 서로 중첩됨 
	그러므로 이벤트 전파를 막아야함
<template>
	<div>
		<div id="modifiers">
			<div @click="clickDiv">
				div
				<p @click="clickP">
					p
					<span @click="clickSpan"> span </span>
				</p>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	setup() {
		const clickDiv = () => {
			console.log('Div');
			location.href = 'https://naver.com';
		};
		const clickP = () => {
			console.log('P');
		};
		const clickSpan = () => {
			console.log('Span');
			alert('좋아요');
		};
		return {
			clickDiv,
			clickP,
			clickSpan,
		};
	},
};
</script>

<style scoped>
#modifiers div,
#modifiers p,
#modifiers span {
	padding: 40px;
}
#modifiers div {
	background-color: tomato;
}
#modifiers p {
	background-color: aquamarine;
}
#modifiers span {
	background-color: bisque;
	display: block;
}
</style> -->
