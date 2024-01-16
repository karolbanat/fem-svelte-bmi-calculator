<script lang="ts">
	export let icon: string;
	export let title: string = '[Title]';
	export let text: string = '[Text]';
</script>

<article>
	<h3>
		<img src={icon} alt="" />
		<span>{title}</span>
	</h3>
	<p>{text}</p>
</article>

<style>
	article {
		display: grid;
		gap: 1rem;

		padding: clamp(var(--spacer-rem-300), 4vw, var(--spacer-rem-400));

		background-color: var(--clr-neutral-100);
		border-radius: var(--borr-400);
		box-shadow: var(--dropshadow-200);
	}

	h3 {
		display: inline-flex;
		align-items: center;
		gap: 1rem;
	}
</style>
