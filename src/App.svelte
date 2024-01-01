<script lang="ts">
	import BMIForm from './lib/BMIForm.svelte';
	import Navigation from './lib/Navigation.svelte';
</script>

<header class="wrapper-grid">
	<Navigation />
	<div class="even-columns-screen vertical-center-grid">
		<div class="flow">
			<h1>Body Mass Index Calculator</h1>
			<p>
				Better understand your weight in relation to your height using our body mass index (BM) calculator. While BMI is
				not the sole determinant of a healthy weight, it offers a valuable starting point to evaluate your overall
				health and well-being.
			</p>
		</div>
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
