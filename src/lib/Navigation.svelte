<script lang="ts">
	import Logo from '/src/images/icons/logo.svg';
</script>

<nav>
	<a href="#" aria-label="Home page">
		<img src={Logo} alt="" />
	</a>
</nav>

<style>
	nav {
		padding-block-start: clamp(var(--spacer-rem-400), 7vw - 1.75rem, var(--spacer-rem-900));
		padding-block-end: clamp(var(--spacer-rem-300), 5.25vw, var(--spacer-rem-500));
	}

	a {
		display: inline-block;
	}

	@media (max-width: 62em) {
		nav {
			text-align: center;
		}
	}

	@media (min-width: 62em) {
		nav {
			padding-block-end: var(--spacer-rem-300);
		}
	}
</style>
