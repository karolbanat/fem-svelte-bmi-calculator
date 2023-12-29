<script lang="ts"></script>

<output>
	<p class="heading">Welcome!</p>
	<p>Enter your height and weight and you'll see your BMI result here</p>
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
