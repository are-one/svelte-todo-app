<script>
</script>

<div class="container is-fullhd is-fluid">
	<h1 class="is-size-3">TODO APP</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	<div class="columns">
		<div class="column is-4">
			<div class="card has-background-light">
				<div class="card-header">
					<div class="card-header-title">Task</div>
				</div>
				<div class="card-content">
					<p>Belajar HTML</p>
					<p>Belaj Javascript</p>
					<p>Belaj Svelte</p>
				</div>
			</div>
		</div>

	</div>
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

</style>