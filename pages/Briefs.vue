<template>
	<div class="credits-page">
		<HomeHeader />
		<FixedPanel />
		<Briefs />
        <BackgroundGrid />
        <MenuBottom />
	</div>
</template>

<script setup>
import transitionConfig from '@/helpers/transitionConfig';
import HomeHeader from '@/components/HomeHeader.vue';
import FixedPanel from '@/components/FixedPanel.vue';
import Briefs from '@/components/Briefs.vue';
import BackgroundGrid from '@/components/BackgroundGrid.vue';
import MenuBottom from '@/components/MenuBottom.vue';

definePageMeta({
	pageTransition: transitionConfig,
});


</script>

<style scoped lang="scss">
.credits-page{
	position: relative;
}
</style>