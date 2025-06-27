<template>
	<div class="briefPage">
		<BackgroundGridCustom />
		<div class="container-title">
			<h2 class="title">NewLeaf</h2>
			<div class="key-words">
				<p class="hero-content">(6 teams)</p>
				<p>11/08/24</p>
			</div>
		</div>
		<div class="container-description">
			<div>
				<h3 class="title">
					Context
				</h3>
				<p class="">
					New Leaf, formé en 2019, est un groupe dont le genre musical est [à vous de choisir]. Ils prévoient un world tour qui passera par différentes villes à
					travers le monde entier. Le groupe souhaite mettre en place un site promotionnel pour cet événement, reflétant leur identité unique,
					tout en laissant au designer la possibilité de proposer une direction artistique qui les reflète.
				</p>
			</div>
			<button class="btn">
				<span class="button-text">brief</span>
				<svg width="8" height="10" viewBox="0 0 8 10" fill="none" xmlns="http://www.w3.org/2000/svg">
					<path fill-rule="evenodd" clip-rule="evenodd" d="M4.0002 0.699951C4.16588 0.699951 4.3002 0.834264 4.3002 0.999951V5.60902L5.7881 4.12115C5.90523 4.00399 6.09516 4.00399 6.2123 4.12115C6.3295 4.23831 6.3295 4.42826 6.2123 4.54542L4.21233 6.54542C4.09517 6.66257 3.90522 6.66257 3.78806 6.54542L1.78806 4.54542C1.6709 4.42826 1.6709 4.23831 1.78806 4.12115C1.90522 4.00399 2.09517 4.00399 2.21233 4.12115L3.7002 5.60902V0.999951C3.7002 0.834264 3.83451 0.699951 4.0002 0.699951ZM0.666829 6.66663C0.850923 6.66663 1.00016 6.81589 1.00016 6.99996V7.99996C1.00016 8.36923 1.29726 8.66663 1.6644 8.66663H6.33429C6.7021 8.66663 7.00016 8.36849 7.00016 7.99996V6.99996C7.00016 6.81589 7.14943 6.66663 7.3335 6.66663C7.51756 6.66663 7.66683 6.81589 7.66683 6.99996V7.99996C7.66683 8.73603 7.07096 9.33329 6.33429 9.33329H1.6644C0.926956 9.33329 0.333496 8.73529 0.333496 7.99996V6.99996C0.333496 6.81589 0.482736 6.66663 0.666829 6.66663Z" fill="white"/>
				</svg>
			</button>
		</div>
		<div class="container-groups">
			<CardGroups v-for="i in 12" :key="i"/>
		</div>
	</div>
</template>
<script setup>
import { useRoute } from 'vue-router'
import transitionConfig from '@/helpers/transitionConfig';

const route = useRoute();
const slug = route?.params?.slug;

definePageMeta({
  pageTransition: transitionConfig,
  layout: 'brief',
  head: {
	title: slug,
	meta: [
	  {
		name: 'description',
		content: 'Brief page for ' + slug,
	  },
	],
  },
});
</script>

<style scoped lang="scss">
.briefPage {
	position: relative;
	z-index: 20;
	width: 100vw;
	max-height: 100vh;
	height: 100vh;
	background: $white;
	display: grid;
	grid-template-columns: repeat(8, minmax(0, 1fr));
	grid-template-rows: repeat(4, minmax(0, 1fr));
	grid-gap: 16px;

	@include mobile-only {
		min-height: 100vh;
		height: 100%;
		grid-template-columns: repeat(2, minmax(0, 1fr));
		grid-template-rows: 22.1vh 24.5vh auto auto;
	}

	.container-title {
		grid-column-start: 1;
		grid-row-start: 2;
		grid-row-end: 2;
		grid-column-end: 4;
		padding: 16px 0 0 16px;
		width: fit-content;
		text-align: center;
		display: flex;
		align-items: center;
		flex-direction: column;

		@include large {
			grid-column-start: 2;
			grid-column-end: 4;
			grid-row-start: 2;
			grid-row-end: 2;
			grid-template-columns: repeat(4, minmax(0, 1fr));
			height: fit-content;
		}

		@include mobile-only {
			grid-column-start: 1;
			grid-column-end: 2;
			grid-row-start: 1;
			grid-row-end: 1;
			padding: 16px 0 0 16px;
		}

		.title {
			position: relative;
			z-index: 10;
			padding-top: 10px;
			color: $black;
			font-size: 100rem;
			line-height: 0.8em;
			@include ppeditorialnew(500);
		}

		.key-words {
			display: flex;
			width: 100%;
			justify-content: space-between;
			color: $black;

			p {
				opacity: 60%;
				font-size: 12rem;
				line-height: 1.1;
				@include ppeditorialnew(400);
			}
		}
	}

	.container-description{
		grid-column-start: 1;
		grid-row-start: 3;
		grid-row-end: 4;
		grid-column-end: 4;
		position: relative;
		z-index: 20;
		display: flex;
		padding: 0 0 10px 16px;
		flex-direction: column;
		justify-content: space-between;

		@include large {
			grid-template-columns: repeat(4, minmax(0, 1fr));
			grid-column-start: 2;
			grid-row-start: 3;
			grid-row-end: 4;
			grid-column-end: 4;
			padding: 0 0 10px 13px;
		}

		@include mobile-only {
			grid-row-start: 2;
			grid-row-end: 3;
			grid-column-end: 3;
			padding: 16px 16px 0 16px;
		}

		.title {
			font-size: 12rem;
			color: $black;
			margin-bottom: 16px;
			text-transform: uppercase;
			@include ppneuemontreal(400);
		}

		p {
			font-size: 12rem;
			color: $black;
			line-height: 1.5;
			opacity: 0.5;
			@include ppneuemontreal(400);
		}
	}

	.btn {
		display: flex;
		align-items: center;
		padding: 10rem 16rem;
		background: $black;
		color: $white;
		width: fit-content;

		.button-text{
			font-size: 10rem;
			@include ppneuemontreal(500);
			text-transform: uppercase;
		}

		svg {
			width: 10rem;
			height: 10rem;
			margin-left: 8rem;
		}
	}

	.container-groups {
		grid-column-start: 5;
		grid-row-start: 1;
		grid-row-end: 5;
		grid-column-end: 9;
		width: 100%;
		background: $black;
		display: grid;
		overflow: scroll;
		grid-template-columns: repeat(1, minmax(0, 1fr));
		grid-template-rows: auto;
		overflow-y: auto;
		overflow-x : hidden;
		gap: 16px;
		padding: 16px;
		min-height: 100vh;

		@include large {
			grid-template-columns: repeat(2, minmax(0, 1fr));
		}

		@include mobile-only {
			grid-column-start: 1;
			grid-column-end: 3;
			grid-row-start: 3;
			grid-row-end: 5;
			overflow-y: visible;
		}
	}
}
</style>