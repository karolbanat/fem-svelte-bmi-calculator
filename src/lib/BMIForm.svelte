<script lang="ts">
	let unit: 'metric' | 'imperial' = 'metric';
</script>

<form>
	<p class="form-heading">Enter your details below</p>

	<fieldset>
		<div class="custom-radio-input">
			<input type="radio" name="measurement-unit" id="metric" checked={unit === 'metric'} />
			<label for="metric">
				<span>Metric</span>
			</label>
		</div>
		<div class="custom-radio-input">
			<input type="radio" name="measurement-unit" id="imperial" checked={unit === 'imperial'} />
			<label for="imperial">
				<span>Imperial</span>
			</label>
		</div>
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

<style></style>
