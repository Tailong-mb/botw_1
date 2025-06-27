<template>
    <div class="background-grid">
        <div class="grid-item" v-for="i in 8" :key="`mobile-${i}`"></div>
        <div class="grid-item hide-mobile" v-for="i in 16" :key="`tablet-${i}`"></div>
        <div class="grid-item hide-tablet" v-for="i in 8" :key="`desktop-${i}`"></div>
    </div>
</template>

<style scoped lang="scss">
.background-grid{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    padding: 8rem;
    display: grid;
	grid-template-columns: repeat(2, minmax(0, 1fr));
    grid-template-rows: repeat(4, minmax(0, 1fr));
    gap:8rem;
    pointer-events: none;
    height: 100vh;

	@include tablet {
		grid-template-columns: repeat(6, minmax(0, 1fr));
	}

	@include desktop {
		grid-template-columns: repeat(8, minmax(0, 1fr));
	}
    
    .grid-item {
        width: 100%;
        height: 100%;
        border: 1px solid rgb($white, 0.1);
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