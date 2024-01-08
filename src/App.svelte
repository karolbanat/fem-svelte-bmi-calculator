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
<main class="wrapper-grid">
	<section class="meaning-section even-columns-screen even-columns-screen--medium vertical-end-grid">
		<img
			src="/assets/images/image-man-eating.webp"
			alt="Smiling man holding chopsticks with sushi roll."
			class="meaning-section__image"
		/>
		<HeaderBox
			headingLevel="h2"
			headingText="What your BMI result means"
			message="A BMI range of 18.5 to 24.9 is considered a 'healthy weight.' Maintaining a healthy weight may lower your chances of experiencing health issues later on, such as obesity and type 2 diabetes. Aim for a nutritious diet with reduced fat and sugar content, incorporating ample fruits and vegetables. Additionally, strive for regular physical activity, ideally about 30 minutes daily for five days a week."
			paddedLeft={true}
		/>
	</section>
</main>

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

	.meaning-section {
		margin-block: clamp(4.5rem, 12.5rem, 6rem);
	}

	@media (min-width: 42em) and (max-width: 62em) {
		.meaning-section__image {
			justify-self: end;
			max-width: 125%;
		}
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
