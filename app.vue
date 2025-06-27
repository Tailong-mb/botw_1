<template>
	<Loader />	
	<NuxtPage />
</template>

<script setup>
import Loader from '@/components/Loader.vue';
import { LOADER_PLAYED } from '@/utils/constant';

const route = useRoute();

onMounted(() => {
	if (route.path !== '/') {
		LOADER_PLAYED.PLAYED = 'true';
	}
})
</script>

<style lang="scss">
html {
	font-size: calc(max(100vw / 360, 1px));

	@include tablet {
		font-size: calc(max(100vw / 768, 1px));
	}

	@include desktop {
		font-size: 1px;
	}

	@include large {
		font-size: calc(max(100vw / 1441, 1px));
	}
}

body {
	background-color: $black;
}
</style>
