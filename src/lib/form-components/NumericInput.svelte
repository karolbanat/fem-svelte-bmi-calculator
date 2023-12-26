<script lang="ts">
	export let unitShortcut: string;
	export let value: number;
	export let name: string;
	export let id: string;
	export let step: number = 1;
</script>

<div class="input-container">
	<input type="number" {name} {id} bind:value {step} />
	<span>{unitShortcut}</span>
</div>

<style>
	.input-container {
		--padding-inline: var(--spacer-rem-300);
		--padding-block: 1.25rem;

		position: relative;

		font-size: var(--fz-600);
		font-weight: var(--fw-bold);
		line-height: 1.1;
	}

	input {
		width: 100%;
		max-width: 100%;

		padding-block: var(--padding-block);
		padding-inline-start: var(--padding-inline);
		padding-inline-end: calc(var(--padding-inline) + 3rem);

		border: 1px solid var(--clr-neutral-400);
		border-radius: 0.75rem;

		appearance: textfield;

		transition: border-color 350ms ease-in-out;
	}

	input::-webkit-outer-spin-button,
	input::-webkit-inner-spin-button {
		appearance: none;
	}

	input:is(:hover, :focus-visible) {
		outline: 1px solid var(--clr-primary-400);

		border-color: var(--clr-primary-400);
		cursor: pointer;
	}

	span {
		position: absolute;
		top: 50%;
		right: var(--padding-inline);
		transform: translateY(-50%);

		color: var(--clr-primary-400);
		pointer-events: none;
	}
</style>
