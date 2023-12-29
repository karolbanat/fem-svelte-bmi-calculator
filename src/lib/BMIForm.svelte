<script lang="ts">
	import type { Unit } from '../types';
	import BmiOutput from './form-components/BMIOutput.svelte';
	import NumericInput from './form-components/NumericInput.svelte';
	import RadioButton from './form-components/RadioButton.svelte';

	let unit: Unit = 'metric';
	let centimeters: number;
	let kilograms: number;

	let feet: number;
	let inches: number;
	let stones: number;
	let pounds: number;
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
					/>
				{:else}
					<NumericInput label="Feet" id="height-ft" name="height-ft" max={10} bind:value={feet} unitShortcut="ft" />
					<NumericInput label="Inches" id="height-in" name="height-in" max={11} bind:value={inches} unitShortcut="in" />
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
					/>
				{:else}
					<NumericInput
						label="Stones"
						id="weight-st"
						name="weight-st"
						max={150}
						bind:value={stones}
						unitShortcut="st"
					/>
					<NumericInput
						label="Pounds"
						id="weight-lbs"
						name="weight-lbs"
						max={13}
						bind:value={pounds}
						unitShortcut="lbs"
					/>
				{/if}
			</div>
		</fieldset>
	</div>

	<BmiOutput />
</form>

<style>
	form {
		display: grid;
		gap: clamp(var(--spacer-rem-300), 4vw, var(--spacer-rem-400));
	}
	fieldset {
		border: none;
	}

	fieldset > legend {
		margin-block-end: var(--spacer-rem-100, 0.5em);
		font-size: var(--fz-300);
	}
</style>
