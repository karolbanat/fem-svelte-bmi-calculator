<script lang="ts">
	export let icon: string;
	export let title: string = '';
	export let text: string = '';
</script>

<article>
	<img src={icon} alt="" class="card-icon" />
	<div class="card-body">
		<h3>{title}</h3>
		<p>{text}</p>
	</div>
</article>

<style>
	article {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: clamp(var(--spacer-rem-400), 5vw, var(--spacer-rem-600));
	}

	h3 {
		font-size: var(--fz-600);
		line-height: 1.1;
	}

	.card-body {
		display: grid;
		gap: var(--spacer-rem-300);
	}

	@media (min-width: 36em) and (max-width: 56em) {
		article {
			flex-direction: row;
			align-items: center;
		}
	}
</style>
