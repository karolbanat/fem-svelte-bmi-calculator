<script lang="ts">
	export let name: string;
	export let value: string;
	export let id: string;
	export let checked: boolean = false;
	export let label: string;

	export let selectedValue: string;
</script>

<div>
	<input type="radio" {name} {value} {id} {checked} bind:group={selectedValue} />
	<label for={id}>
		<span>{label}</span>
	</label>
</div>

<style>
	div {
		display: flex;
		align-items: center;
		gap: 1.125rem;
	}

	label {
		font-weight: var(--fw-bold);
		color: var(--clr-primary-700);
	}

	input[type='radio'] {
		--_width: 30px;
		--_border-width: 1px;
		appearance: none;

		display: inline-grid;
		place-content: center;

		width: var(--_width);
		aspect-ratio: 1 / 1;

		border-radius: 50%;
		border: var(--_border-width) solid var(--clr-neutral-400);

		transition: border-color 350ms ease-in-out;
	}

	input[type='radio']::before {
		content: '';
		width: calc(var(--_width) - 2 * var(--_border-width));
		aspect-ratio: 1 / 1;

		border-radius: inherit;
		background-color: var(--clr-neutral-100);
	}

	input[type='radio']:is(:hover, :focus-visible),
	label {
		border-color: var(--clr-primary-400);
		cursor: pointer;
	}

	input[type='radio']:checked {
		--_border-width: 8px;
		border-color: hsl(var(--clr-primary-400-hsl) / 0.15);
	}

	input[type='radio']:checked::before {
		background-color: var(--clr-primary-400);
	}
</style>
