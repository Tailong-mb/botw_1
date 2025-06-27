<template>
	<div class="credits-page">
		<HomeHeader />
		<FixedPanel />
		<Credits />
		<BackgroundGrid />
		<MenuBottom />
	</div>
</template>

<script setup>
import transitionConfig from '@/helpers/transitionConfig';
import HomeHeader from '@/components/HomeHeader.vue';
import FixedPanel from '@/components/FixedPanel.vue';
import Credits from '@/components/Credits.vue';
import MenuBottom from '@/components/MenuBottom.vue';

definePageMeta({
	pageTransition: transitionConfig,
});
</script>

<style scoped lang="scss">
.credits-page{
	position: relative;
	min-height: 100vh;
}
</style>