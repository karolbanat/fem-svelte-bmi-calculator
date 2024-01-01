<script lang="ts">
	import type { Heading } from '../types';

	export let headingLevel: Heading = 'h1';
	export let headingText: string = 'Insert your heading here';
	export let message: string = 'Message goes here';

	export let centered: boolean = false;
	export let paddedLeft: boolean = false;
	export let paddedRight: boolean = false;
</script>

<div class="flow" class:centered class:padded-left={paddedLeft} class:padded-right={paddedRight}>
	<svelte:element this={headingLevel} class="heading">{headingText}</svelte:element>
	<p>{message}</p>
</div>

<style>
	.heading {
		margin-block-end: clamp(var(--spacer-rem-300), 4vw, var(--spacer-rem-450));
	}

	@media (max-width: 56em) {
		.centered {
			text-align: center;
		}
	}

	@media (min-width: 56em) {
		.padded-right {
			padding-inline-end: clamp(2rem, 7.5vw, 6.25rem);
		}

		.padded-left {
			padding-inline-start: clamp(2rem, 7.5vw, 6.25rem);
		}
	}
</style>
