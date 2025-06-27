<template>
	<div class="grid-background">
		<div class="grid-item" v-for="i in 8" :key="`mobile-${i}`"></div>
        <div class="grid-item hide-mobile" v-for="i in 16" :key="`tablet-${i}`"></div>
        <div class="grid-item hide-tablet" v-for="i in 8" :key="`desktop-${i}`"></div>
	</div>
</template>

<style scoped lang="scss">
.grid-background {
	position: absolute;
	padding: 8rem;
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	grid-template-rows: repeat(4, 1fr);
	gap: 8rem;
	height: 100vh;
	width: 100%;

	@include desktop {
		grid-template-columns: repeat(4, 1fr);
	}

	@include large {
		grid-template-columns: repeat(8, 1fr);
	}

	.grid-item {
		width: 100%;
		height: 100%;
		border: 1px solid rgb($black, 0.05);
	}
	
	.hide-mobile{
		display: none;
	
		@include tablet{
			display: block;
		}
	}
	
	.hide-tablet{
		display: none;
	
		@include desktop{
			display: block;
		}
	}   
}

</style>