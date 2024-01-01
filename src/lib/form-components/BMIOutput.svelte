<script lang="ts">
	import { roundToTwoDecimals } from '../../utils/utils';

	export let kilograms: number = 0;
	export let centimeters: number = 0;

	$: calculateBMI = () => kilograms / Math.pow(centimeters / 100, 2);
</script>

<output>
	{#if kilograms === 0 || centimeters == 0}
		<p class="heading">Welcome!</p>
		<p>Enter your height and weight and you'll see your BMI result here</p>
	{:else}
		<div class="even-columns-fluid" style="--fluid-size: 10rem">
			<div>
				<p>Your BMI is...</p>
				<p class="bmi-result">{roundToTwoDecimals(calculateBMI())}</p>
			</div>
			<div>
				<p>Your BMI suggests you're a healthy weight. Your ideal weight is between 63.3kgs - 85.2kgs.</p>
			</div>
		</div>
	{/if}
</output>

<style>
	output {
		position: relative;
		isolation: isolate;

		display: block;
		padding: var(--spacer-rem-400);

		font-size: var(--fz-300);

		color: var(--clr-neutral-100);

		border-radius: 1rem;
		overflow: hidden;
	}

	output::before {
		content: '';
		position: absolute;
		z-index: -1;
		inset: 0;
		width: 100%;
		height: 100%;

		background-image: var(--gradient-600);

		border-radius: inherit;
	}

	.heading {
		margin-block-end: var(--spacer-em-200, 1em);

		font-size: var(--fz-600);
		font-weight: var(--fw-bold);
		line-height: 1.1;
		letter-spacing: -0.05em;
	}

	@media (min-width: 36em) {
		output::before {
			border-top-right-radius: var(--borr-pill);
			border-bottom-right-radius: var(--borr-pill);
		}
	}
</style>
