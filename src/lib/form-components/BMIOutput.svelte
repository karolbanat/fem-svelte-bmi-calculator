<script lang="ts">
	import { roundToTwoDecimals } from '../../utils/utils';

	export let kilograms: number = 0;
	export let centimeters: number = 0;

	const classifications = [
		{
			lowerBound: 0,
			upperBound: 18.5,
			name: 'underweight',
		},
		{
			lowerBound: 18.5,
			upperBound: 24.9,
			name: 'healthy weight',
		},
		{
			lowerBound: 25,
			upperBound: 29.9,
			name: 'overweight',
		},
		{
			lowerBound: 30,
			name: 'obese',
		},
	];

	$: lowerHealthyWeight = roundToTwoDecimals(18.5 * Math.pow(centimeters / 100, 2));
	$: upperHealthyWeight = roundToTwoDecimals(24.9 * Math.pow(centimeters / 100, 2));
	$: BMI = kilograms / Math.pow(centimeters / 100, 2);
	$: classification = classifications
		.filter(range => BMI >= range.lowerBound && BMI <= (range.upperBound || Number.MAX_SAFE_INTEGER))
		.at(0);
</script>

<output>
	{#if kilograms === 0 || centimeters == 0}
		<p class="heading">Welcome!</p>
		<p>Enter your height and weight and you'll see your BMI result here</p>
	{:else}
		<div class="even-columns-fluid" style="--fluid-size: 10rem">
			<div>
				<p class="bmi-kicker">Your BMI is...</p>
				<p class="bmi-result">{roundToTwoDecimals(BMI)}</p>
			</div>
			<div>
				<p>
					Your BMI suggests you're {classification?.name}. Your ideal weight is between {lowerHealthyWeight}kgs - {upperHealthyWeight}kgs.
				</p>
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

	.heading,
	.bmi-result {
		font-weight: var(--fw-bold);
		line-height: 1.1;
		letter-spacing: -0.05em;
	}
	.heading {
		margin-block-end: var(--spacer-em-200, 1em);

		font-size: var(--fz-600);
	}

	.bmi-kicker {
		font-size: var(--fz-400);
		font-weight: var(--fw-bold);
	}

	.bmi-result {
		margin-block-end: var(--spacer-rem-100, 0.5em);
		font-size: var(--fz-800);
	}

	@media (min-width: 36em) {
		output::before {
			border-top-right-radius: var(--borr-pill);
			border-bottom-right-radius: var(--borr-pill);
		}
	}
</style>
