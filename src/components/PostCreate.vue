<template>
	<div class="row g-3">
		<div class="col col-2">
			<select
				v-model="type"
				class="form-select"
				aria-label="Default select example"
			>
				<option value="news" selected>뉴스</option>
				<option value="notice">공지사항</option>
			</select>
		</div>
		<div class="col col-8">
			<input v-model="title" class="form-control" type="text" />
		</div>
		<div class="col col-2 d-grid">
			<button class="btn btn-primary" @click="createPost">추가</button>
		</div>

		<!-- <button
			class="btn btn-primary"
			@click="$emit('create-post', 1, 2, 3, '김길동')"
		> -->
	</div>
</template>

<script>
import { ref } from 'vue';
export default {
	emits: {
		// ['createPost'],
		// createPost: newTitle => {
		// 	console.log('validator:', newTitle);
		// 	if (!newTitle) {
		// 		return false;
		// 	}
		// 	return true;
		// },
		//null//유효성 없으면

		createPost: newPost => {
			if (!newPost.type) {
				return false;
			} else if (!newPost.title) {
				return false;
			}
			return true;
		},
	},
	setup(props, context) {
		//context.emit
		const title = ref('');
		const type = ref('news');
		const createPost = () => {
			// context.emit('createPost', 111, 2, 3, '김길동');
			const newPost = {
				type: type.value,
				title: title.value,
			};
			context.emit('createPost', newPost);
			type.value = 'news';
			title.value = '';
		};

		return { createPost, title, type };
	},
};
</script>

<style lang="scss" scoped></style>
