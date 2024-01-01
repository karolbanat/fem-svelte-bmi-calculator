<script lang="ts">
	import type { Unit } from '../types';
	import { roundToNthDecimal } from '../utils/utils';
	import BmiOutput from './form-components/BMIOutput.svelte';
	import NumericInput from './form-components/NumericInput.svelte';
	import RadioButton from './form-components/RadioButton.svelte';

	const STONE: number = 6.35029318;
	const POUNDS_IN_STONE: number = 14;

	const FOOT: number = 30.48;
	const INCHES_IN_FEET: number = 12;

	let unit: Unit = 'metric';
	let centimeters: number = 0;
	let kilograms: number = 0;

	let feet: number = 0;
	let inches: number = 0;
	let stones: number = 0;
	let pounds: number = 0;

	function convertKilograms() {
		const kgToStones: number = roundToNthDecimal(kilograms / STONE);
		stones = Math.floor(kgToStones);
		pounds = Math.round((kgToStones - stones) * POUNDS_IN_STONE);
	}

	function convertCentimeters() {
		const cmToFeet: number = roundToNthDecimal(centimeters / FOOT);
		feet = Math.floor(cmToFeet);
		inches = Math.round((cmToFeet - feet) * INCHES_IN_FEET);
	}

	function convertStonesAndPounds() {
		const poundsToStone: number = roundToNthDecimal(pounds / POUNDS_IN_STONE);
		kilograms = Math.round((stones + poundsToStone) * STONE);
	}

	function convertFeetAndInches() {
		const inchesToFeet: number = roundToNthDecimal(inches / INCHES_IN_FEET);
		centimeters = Math.round((feet + inchesToFeet) * FOOT);
	}
</script>

<form>
	<p class="form-heading">Enter your details below</p>

	<fieldset class="even-columns">
		<RadioButton
			name="measurement-unit"
			id="metric"
			value="metric"
			checked={unit === 'metric'}
			label="Metric"
			bind:selectedValue={unit}
		/>
		<RadioButton
			name="measurement-unit"
			id="imperial"
			value="imperial"
			checked={unit === 'imperial'}
			label="Imperial"
			bind:selectedValue={unit}
		/>
	</fieldset>

	<div class="even-columns-fluid" style={unit === 'metric' ? '' : '--fluid-size: 1fr;'}>
		<fieldset>
			<legend>Height</legend>
			<div class={unit === 'metric' ? '' : 'even-columns'}>
				{#if unit === 'metric'}
					<NumericInput
						label="Centimeters"
						id="height-cm"
						name="height-cm"
						max={300}
						bind:value={centimeters}
						unitShortcut="cm"
						on:input={convertCentimeters}
					/>
				{:else}
					<NumericInput
						label="Feet"
						id="height-ft"
						name="height-ft"
						max={10}
						bind:value={feet}
						unitShortcut="ft"
						on:input={convertFeetAndInches}
					/>
					<NumericInput
						label="Inches"
						id="height-in"
						name="height-in"
						max={11}
						bind:value={inches}
						unitShortcut="in"
						on:input={convertFeetAndInches}
					/>
				{/if}
			</div>
		</fieldset>
		<fieldset>
			<legend>Weight</legend>
			<div class={unit === 'metric' ? '' : 'even-columns'}>
				{#if unit === 'metric'}
					<NumericInput
						label="Kilograms"
						id="weight-kg"
						name="weight-kg"
						max={1000}
						bind:value={kilograms}
						unitShortcut="kg"
						on:input={convertKilograms}
					/>
				{:else}
					<NumericInput
						label="Stones"
						id="weight-st"
						name="weight-st"
						max={150}
						bind:value={stones}
						unitShortcut="st"
						on:input={convertStonesAndPounds}
					/>
					<NumericInput
						label="Pounds"
						id="weight-lbs"
						name="weight-lbs"
						max={13}
						bind:value={pounds}
						unitShortcut="lbs"
						on:input={convertStonesAndPounds}
					/>
				{/if}
			</div>
		</fieldset>
	</div>

	<BmiOutput kilograms={kilograms || 0} centimeters={centimeters || 0} />
</form>

<style>
	form {
		--_spacer: clamp(var(--spacer-rem-300), 4vw, var(--spacer-rem-400));
		display: grid;
		gap: var(--_spacer);

		padding: var(--_spacer);

		background-color: var(--clr-neutral-100);
		border-radius: var(--borr-400);
		box-shadow: var(--dropshadow-200);
	}
	fieldset {
		border: none;
	}

	fieldset > legend {
		margin-block-end: var(--spacer-rem-100, 0.5em);
		font-size: var(--fz-300);
	}

	.form-heading {
		font-size: var(--fz-600);
		font-weight: var(--fw-bold);
		color: var(--clr-primary-700);
	}
</style>
