<script lang="ts">
	import imageManEating from '/src/images/image-man-eating.webp';

	import iconEating from '/src/images/icons/icon-eating.svg';
	import iconExercise from '/src/images/icons/icon-exercise.svg';
	import iconSleep from '/src/images/icons/icon-sleep.svg';

	import iconGender from '/src/images/icons/icon-gender.svg';
	import iconAge from '/src/images/icons/icon-age.svg';
	import iconMuscle from '/src/images/icons/icon-muscle.svg';
	import iconPregnancy from '/src/images/icons/icon-pregnancy.svg';
	import iconRace from '/src/images/icons/icon-race.svg';

	import BMIForm from './lib/BMIForm.svelte';
	import HeaderBox from './lib/HeaderBox.svelte';
	import Navigation from './lib/Navigation.svelte';
	import TipCard from './lib/cards/TipCard.svelte';
	import LimitationCard from './lib/cards/LimitationCard.svelte';
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
	<section
		class="meaning-section | even-columns-screen even-columns-screen--medium vertical-end-grid | section-spacer curved-line-left"
	>
		<img src={imageManEating} alt="Smiling man holding chopsticks with sushi roll." class="meaning-section__image" />
		<HeaderBox
			headingLevel="h2"
			headingText="What your BMI result means"
			message="A BMI range of 18.5 to 24.9 is considered a 'healthy weight.' Maintaining a healthy weight may lower your chances of experiencing health issues later on, such as obesity and type 2 diabetes. Aim for a nutritious diet with reduced fat and sugar content, incorporating ample fruits and vegetables. Additionally, strive for regular physical activity, ideally about 30 minutes daily for five days a week."
			paddedLeft={true}
		/>
	</section>

	<section class="tips-section | full-width section-spacer">
		<h2 class="visually-hidden">Tips</h2>
		<div class="wrapper-grid">
			<div class="even-columns-screen" style="--even-columns-screen-spacer: var(--spacer-rem-400);">
				<TipCard
					icon={iconEating}
					title="Healthy eating"
					text="Healthy eating promotes weight control, disease prevention, better digestion, immunity, mental clarity, and mood."
				/>
				<TipCard
					icon={iconExercise}
					title="Regular exercise"
					text="Exercise improves fitness, aids weight control, elevates mood, and reduces disease risk, fostering wellness and longevity."
				/>
				<TipCard
					icon={iconSleep}
					title="Adequate sleep"
					text="Sleep enhances mental clarity, emotional stability, and physical wellness, promoting overall restoration and rejuvenation."
				/>
			</div>
		</div>
	</section>

	<section class="limitations-layout | section-spacer curved-line-right">
		<HeaderBox
			headingLevel="h2"
			headingText="Limitations of BMI"
			message="Although BMI is often a practical indicator of healthy weight, it is not suited for every person. Specific groups should carefully consider their BMI outcomes, and in certain cases, the measurement may not be beneficial to use."
			centered={true}
			paddedRight={true}
		/>
		<LimitationCard
			icon={iconGender}
			title="Gender"
			text="The development and body fat composition of girls and boys vary with age. Consequently, a child's age and gender are considered when evaluating their BMI."
		/>
		<LimitationCard
			icon={iconAge}
			title="Age"
			text="In aging individuals, increased body fat and muscle loss may cause BMI to underestimate body fat content."
		/>
		<LimitationCard
			icon={iconMuscle}
			title="Muscle"
			text="BMI may misclassify muscular individuals as overweight or obese, as it doesn't differentiate muscle from fat."
		/>
		<LimitationCard
			icon={iconPregnancy}
			title="Pregnancy"
			text="Expectant mothers experience weight gain due to their growing baby. Maintaining a healthy pre-pregnancy BMI is advisable to minimise health risks for both mother and child."
		/>
		<LimitationCard
			icon={iconRace}
			title="Race"
			text="Certain health concerns may affect individuals of some Black and Asian origins at lower BMIs than others. To learn more, it is advised to discuss this with your GP or practice nurse."
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
		margin-block-start: var(--section-spacer);
	}

	.tips-section {
		position: relative;
		isolation: isolate;

		padding-block-start: clamp(var(--spacer-rem-700), 7.5vw, var(--spacer-rem-900));
		padding-block-end: clamp(var(--spacer-rem-700), 7.5vw, 6rem);
	}

	.tips-section::before {
		content: '';
		position: absolute;
		inset: 0;
		z-index: -1;

		background-image: var(--gradient-400);
		opacity: 0.25;
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

		.tips-section::before {
			inset: 0 var(--spacer-rem-300);
			border-radius: var(--borr-600);
		}
	}
</style>
