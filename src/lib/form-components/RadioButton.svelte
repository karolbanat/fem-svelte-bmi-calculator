<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	export let name: string;
	export let value: string;
	export let id: string;
	export let checked: boolean = false;
	export let label: string;

	function onChange() {
		dispatch('change', {
			value,
		});
	}
</script>

<div>
	<input type="radio" {name} {value} {id} {checked} on:change={onChange} />
	<label for={id}>
		<span>{label}</span>
	</label>
</div>

<style></style>
