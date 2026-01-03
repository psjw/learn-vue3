<template>
	<div>
		<h2>보간법</h2>
		<p>{{ messages }}</p>
		<p v-once>{{ messages }}</p>
		<button v-on:click="messages = messages + '!'">Click!</button>
		<hr />
		<h2>HTML</h2>
		<p>{{ rawHtml }}</p>
		<p v-html="rawHtml"></p>
		<hr />
		<h2>속성바인딩</h2>
		<div :title="dynamicTitle">마우스를 올려보세요</div>
		<input type="text" value="홍길동" :disabled="isInputDisabled" />
		<br />
		<input v-bind="attrs" />
		<h2>JavaScript</h2>
		{{ messages.split('').reverse().join('') }}
		<br />
		{{ isInputDisabled ? '예' : '아니오' }}
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const messages = ref('안녕하세요');
		const rawHtml = ref('<strong>안녕하세요</strong>');

		const dynamicTitle = ref('안녕하세요!!!@@@');
		const isInputDisabled = ref(true);
		const attrs = {
			type: 'text',
			value: '12345678',
			disabled: false,
		};
		return {
			messages,
			rawHtml,
			dynamicTitle,
			isInputDisabled,
			attrs,
		};
	},
};
</script>

<style lang="scss" scoped></style>
