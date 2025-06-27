<template>
	<div class="container-groups-wrapper">
		<div class="left">
			<div class="container-design">
				<div class="container-inner">
					<span class="pseudo">
						Sewon
					</span>
					<div class="link">
						Figma
						<svg xmlns="http://www.w3.org/2000/svg" width="10" height="10" viewBox="0 0 10 10" fill="none">
							<g opacity="0.5">
								<path fill-rule="evenodd" clip-rule="evenodd" d="M2.43113 2.43089C2.30095 2.56106 2.30095 2.77211 2.43113 2.90229L6.8621 7.33326H4.00016C3.81607 7.33326 3.66683 7.48253 3.66683 7.66659C3.66683 7.85066 3.81607 7.99993 4.00016 7.99993H7.66683C7.75523 7.99993 7.84003 7.96479 7.90256 7.90233C7.96503 7.83979 8.00016 7.75499 8.00016 7.66659V3.99992C8.00016 3.81583 7.8509 3.66659 7.66683 3.66659C7.48276 3.66659 7.3335 3.81583 7.3335 3.99992V6.86186L2.90253 2.43088C2.77236 2.30071 2.5613 2.30071 2.43113 2.43089Z" fill="white"/>
							</g>
						</svg>
					</div>
				</div>
				<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16" fill="none">
					<path fill-rule="evenodd" clip-rule="evenodd" d="M12.4746 0.276154C12.2281 0.0296936 11.8285 0.0296936 11.5821 0.276154L2.20167 9.65653C2.08812 9.77008 1.99729 9.90424 1.93403 10.0518L0.0886438 14.3577C-0.0130119 14.595 0.0399869 14.8701 0.22246 15.0526C0.404932 15.235 0.680112 15.288 0.9173 15.1864L5.22321 13.341C5.3708 13.2778 5.50497 13.1869 5.61852 13.0734L14.9989 3.69299C15.2453 3.44654 15.2453 3.04696 14.9989 2.80051L12.4746 0.276154ZM3.09416 10.549L12.0283 1.61489L13.6601 3.24675L4.72602 12.1809L2.83867 12.9897L2.2853 12.4364L3.09416 10.549Z" fill="white"/>
				</svg>
			</div>
			<div class="container-dev">
				<div class="container-inner">
					<span class="pseudo">
						Sewon
					</span>
					<div class="link">
						Website
						<svg xmlns="http://www.w3.org/2000/svg" width="10" height="10" viewBox="0 0 10 10" fill="none">
							<g opacity="0.5">
								<path fill-rule="evenodd" clip-rule="evenodd" d="M2.43113 2.43089C2.30095 2.56106 2.30095 2.77211 2.43113 2.90229L6.8621 7.33326H4.00016C3.81607 7.33326 3.66683 7.48253 3.66683 7.66659C3.66683 7.85066 3.81607 7.99993 4.00016 7.99993H7.66683C7.75523 7.99993 7.84003 7.96479 7.90256 7.90233C7.96503 7.83979 8.00016 7.75499 8.00016 7.66659V3.99992C8.00016 3.81583 7.8509 3.66659 7.66683 3.66659C7.48276 3.66659 7.3335 3.81583 7.3335 3.99992V6.86186L2.90253 2.43088C2.77236 2.30071 2.5613 2.30071 2.43113 2.43089Z" fill="white"/>
							</g>
						</svg>
					</div>
				</div>
				<svg class="icon-dev" width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g opacity="0.21">
						<path fill-rule="evenodd" clip-rule="evenodd" d="M11.9573 3.2229C12.0804 2.91522 11.9307 2.56604 11.623 2.44297C11.3154 2.31991 10.9662 2.46955 10.8431 2.77723L6.04311 14.7772C5.92003 15.0849 6.06969 15.4341 6.37735 15.5571C6.68503 15.6802 7.03421 15.5306 7.15728 15.2229L11.9573 3.2229ZM4.62445 6.1758C4.85878 6.41011 4.85878 6.79001 4.62445 7.02432L2.64873 9.00006L4.62445 10.9758C4.85878 11.2101 4.85878 11.59 4.62445 11.8243C4.39014 12.0586 4.01025 12.0586 3.77593 11.8243L1.37593 9.42432C1.14162 9.19001 1.14162 8.81011 1.37593 8.5758L3.77593 6.1758C4.01025 5.94149 4.39014 5.94149 4.62445 6.1758ZM13.3759 6.1758C13.6102 5.94149 13.9902 5.94149 14.2245 6.1758L16.6245 8.5758C16.8588 8.81011 16.8588 9.19001 16.6245 9.42432L14.2245 11.8243C13.9902 12.0586 13.6102 12.0586 13.3759 11.8243C13.1416 11.59 13.1416 11.2101 13.3759 10.9758L15.3517 9.00006L13.3759 7.02432C13.1416 6.79001 13.1416 6.41011 13.3759 6.1758Z" fill="white"/>
					</g>
				</svg>
			</div>
		</div>
		<div class="right">

		</div>
	</div>
</template>

<script setup>

</script>

<style scoped lang="scss">
.container-groups-wrapper {
	display: grid;
	grid-template-columns: repeat(2, minmax(0, 1fr));
	width: 100%;
	min-width: 300px;

	.left {
		width: 100%;
		height: 100%;

		.container-dev {
			height: 50%;
			background: #191919 !important;
		}

		.container-design, .container-dev{
			display: flex;
			height: 50%;
			width: 100%;
			background: #101010;
			padding: 20px 16px;

			.icon-dev {
				opacity: 0.5 !important;
			}

			svg {
				width: 20rem;
				height: 18rem;
				opacity: 0.1;
				color: #fff;
			}

			.container-inner{
				display: flex;
				align-content: end;
				justify-content: end;
				flex-direction: column;
				height: 100%;
				width: 100%;

				.pseudo{
					font-size: 20rem;
					color: $white;
					@include ppeditorialnew(400);
					margin-right: 16px;
				}

				.link {
					display: flex;
					align-items: center;
					font-size: 8rem;
					color: $white;
					opacity: 0.5;
					letter-spacing: 1rem;
					@include ppneuemontreal(400);
					text-transform: uppercase;

					svg {
						width: 12px;
						height: 12px;
						margin-left: 2px;
						color: $white;
						opacity: 1;
					}
				}
			}
		}
	}

	.right {
		width: 100%;
		height: 100%;
		background: $white;


	}
}
</style>