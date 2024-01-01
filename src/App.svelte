<script lang="ts">
	import BMIForm from './lib/BMIForm.svelte';
	import HeaderBox from './lib/HeaderBox.svelte';
	import Navigation from './lib/Navigation.svelte';
</script>

<header class="wrapper-grid">
	<Navigation />
	<div class="even-columns-screen vertical-center-grid" style="--even-columns-screen-spacer: var(--spacer-rem-400);">
		<HeaderBox
			headingText="Body Mass Index Calculator"
			message="Better understand your weight in relation to your height using our body mass index (BM) calculator. While BMI is
        not the sole determinant of a healthy weight, it offers a valuable starting point to evaluate your overall
        health and well-being."
			centered={true}
			paddedRight={true}
		/>
		<BMIForm />
	</div>
</header>
<main></main>

<style>
	header {
		position: relative;
		isolation: isolate;
	}

	header::before {
		content: '';
		position: absolute;
		z-index: -1;

		width: 100%;
		height: 40rem;

		background-image: var(--gradient-400);
		border-radius: 0 0 var(--borr-600) var(--borr-600);
	}

	@media (min-width: 62em) {
		header {
			padding-block-end: 5.375rem;
		}

		header::before {
			left: var(--spacer-rem-300);

			width: 61.125rem;
			height: 46rem;
		}
	}
</style>
