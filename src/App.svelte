<script lang="ts">
	import BMIForm from './lib/BMIForm.svelte';
	import HeaderBox from './lib/HeaderBox.svelte';
	import Navigation from './lib/Navigation.svelte';
</script>

<header class="wrapper-grid">
	<Navigation />
	<div class="even-columns-screen vertical-center-grid">
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
	@media (min-width: 62em) {
		header {
			padding-block-end: 5.375rem;
		}
	}
</style>
