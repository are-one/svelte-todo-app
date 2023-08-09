<script>
</script>

<div class="container is-fullhd">
	<h1 class="is-size-3">TODO APP</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</div>

<!-- Cara 2 Mengintegrasikan css framework Bulma -->
<svelte:head>
	<link rel="stylesheet" href="/bulma.min.css" />
</svelte:head>

<style>
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>