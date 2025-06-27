<template>
	<div class="home-page">
		<BackgroundGrid />
		<HomeHeader />
		<FixedPanel />
		<Hero />
		<MenuBottom />
	</div>
</template>

<script setup>
import transitionConfig from '@/helpers/transitionConfig';
import FixedPanel from '@/components/FixedPanel.vue';
import Hero from '@/components/Hero.vue';
import BackgroundGrid from '@/components/BackgroundGrid.vue';
import MenuBottom from '@/components/MenuBottom.vue';

definePageMeta({
	pageTransition: transitionConfig,
});

</script>

<style scoped lang="scss">
.home-page{
	position: relative;
	min-height: 100vh;
}
</style>