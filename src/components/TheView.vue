<template>
	<div>
		<main>
			<div class="container py-4">
				<div class="container">
					<div class="row g-3">
						<div class="col-4">
							<AppCard></AppCard>
						</div>
						<div class="col-4"><AppCard></AppCard></div>
						<div class="col-4"><AppCard></AppCard></div>
						<div class="col-4"><AppCard></AppCard></div>
						<div class="col-4"><AppCard></AppCard></div>
						<div class="col-4"><AppCard></AppCard></div>
					</div>
				</div>
			</div>
		</main>
	</div>
</template>

<script>
import AppCard from '@/components/AppCard.vue';
export default {
	components: {
		AppCard,
	},
	setup() {
		return {};
	},
};
</script>

<style lang="scss" scoped></style>
