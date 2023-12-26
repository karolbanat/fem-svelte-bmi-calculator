<script lang="ts">
	import type { Unit } from '../types';
	import NumericInput from './form-components/NumericInput.svelte';
	import RadioButton from './form-components/RadioButton.svelte';

	let unit: Unit = 'metric';
	let centimeters: number;
	let kilograms: number;
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

	<fieldset>
		<div>
			<label for="height">Height</label>
			<NumericInput unitShortcut="cm" id="height" name="height" bind:value={centimeters} />
		</div>
		<div>
			<label for="weight">Weight</label>
			<NumericInput unitShortcut="kg" id="weight" name="weight" bind:value={kilograms} />
		</div>
	</fieldset>

	<output>
		<p>Welcome!</p>
		<p>Enter your height and weight and you'll see your BMI result here</p>
	</output>
</form>

<style>
	form {
		display: grid;
		gap: clamp(var(--spacer-rem-300), 4vw, var(--spacer-rem-400));
	}
	fieldset {
		border: none;
	}
</style>
