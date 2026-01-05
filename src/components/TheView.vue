<template>
	<div>
		<main>
			<div class="container py-4">
				<div class="container">
					<PostCreate @create-post="createPost"></PostCreate>
					<hr class="my-4" />
					<div class="row g-3">
						<!-- <div class="col-4">
							<AppCard title="제목1" contents="내용1"></AppCard>
						</div>
						<div class="col-4">
							<AppCard :title="post.title" :contents="post.contents"></AppCard>
						</div> -->
						<div class="col-4" v-for="post in posts" :key="post.id">
							<AppCard
								:title="post.title"
								:contents="post.contents"
								:type="post.type"
								:is-like="post.isLike"
								@toggle-like="post.isLike = !post.isLike"
							></AppCard>
							<!--부모-> 자식은 변경되나 자식 -> 부모 변경안됨-->
							<button @click="post.isLike = !post.isLike">toggle</button>
						</div>
					</div>

					<hr class="my-4" />
					<!--
						modelValue
						update:modelValue
					-->
					<!-- <LabelInput
						:model-value="username"
						@update:model-value="value => (username = value)"
					></LabelInput> -->
					<LabelInput v-model="username" label="이름"></LabelInput>
					<LabelTitle v-model:title="username" label="제목"></LabelTitle>
					<Username
						v-model:firstname="firstname"
						v-model:lastname="lastname"
					></Username>
				</div>
			</div>
		</main>
	</div>
</template>

<script>
import AppCard from '@/components/AppCard.vue';
import PostCreate from '@/components/PostCreate.vue';
import LabelInput from '@/components/LabelInput.vue';
import LabelTitle from '@/components/LabelTitle.vue';
import Username from '@/components/Username.vue';
import { reactive, ref } from 'vue';
export default {
	components: {
		AppCard,
		PostCreate,
		LabelInput,
		LabelTitle,
		Username,
	},
	setup() {
		const post = reactive({
			title: '제목2',
			contents: '내용2',
		});

		const posts = reactive([
			{ id: 1, title: '제목1', contents: '내용1', isLike: true, type: 'news' },
			{ id: 2, title: '제목2', contents: '내용2', isLike: true, type: 'news' },
			{ id: 3, title: '제목3', contents: '내용3', isLike: true, type: 'news' },
			{
				id: 4,
				title: '제목4',
				contents: '내용4',
				isLike: false,
				type: 'notice',
			},
			{
				id: 5,
				title: '제목5',
				contents: '내용5',
				isLike: false,
				type: 'notice',
			},
		]);

		// const createPost = (a, b, c, d) => {
		// 	console.log('createPost', a, b, c, d);
		// };
		const createPost = newPost => {
			console.log('createPost');
			console.log('newPost', newPost);
			posts.push(newPost);
		};
		const username = ref('');
		const firstname = ref('');
		const lastname = ref('');
		return {
			post,
			posts,
			createPost,
			username,
			firstname,
			lastname,
		};
	},
};
</script>

<style lang="scss" scoped></style>
