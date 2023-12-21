<script lang="ts">
	import RadioButton from './form-components/RadioButton.svelte';

	type Unit = 'metric' | 'imperial';

	let unit: Unit = 'metric';

	function handleChange(event: { detail: { value: string } }) {
		unit = event.detail.value as Unit;
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
			on:change={handleChange}
		/>
		<RadioButton
			name="measurement-unit"
			id="imperial"
			value="imperial"
			checked={unit === 'imperial'}
			label="Imperial"
			on:change={handleChange}
		/>
	</fieldset>

	<fieldset>
		<div>
			<label for="height">Height</label>
			<input type="number" min="0" step="1" placeholder="0" id="height" />
		</div>
		<div>
			<label for="weight">Weight</label>
			<input type="number" min="0" step="1" placeholder="0" id="weight" />
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
