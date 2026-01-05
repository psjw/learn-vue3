<template>
	<div>
		<label>
			이름
			<!-- v-model="username" -->
			<input v-model="value" type="text" />
			<!-- :value="modelValue"
      @input="event => $emit('update:modelValue', event.target.value)" -->
		</label>
	</div>
</template>

<script>
import { computed } from 'vue';
export default {
	props: ['modelValue', 'label'],
	emits: ['update:modelValue'],
	setup(props, { emit }) {
		const value = computed({
			get() {
				return props.modelValue;
			},
			set(value) {
				console.log('set', value);
				emit('update:modelValue', value);
			},
		});
		return { value };
	},
};
</script>

<style lang="scss" scoped></style>
