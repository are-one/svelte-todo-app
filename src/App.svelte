<script>
</script>

<div class="container is-fullhd is-fluid">
	<h1 class="is-size-3">TODO APP</h1>

	<div class="columns">
		<div class="column is-4">
			<div class="card has-background-light">
				<div class="card-header">
					<div class="card-header-title">Task</div>
				</div>
				<div class="card-content">
					<div class="card mb-3 has-background-primary-light">
						<div class="card-content">
							<p class="has-text-primary-dark">Belajar HTML</p>
						</div>
					</div>
					<div class="card mb-3 has-background-primary-light">
						<div class="card-content">
							<p class="has-text-primary-dark">Belajar CSS Framework Bulma</p>
						</div>
					</div>
					<div class="card mb-3 has-background-primary-light">
						<div class="card-content">
							<p class="has-text-primary-dark">Belajar Javascript</p>
						</div>
					</div>
					<div class="card has-background-primary-light">
						<div class="card-content">
							<p class="has-text-primary-dark">Belajar Svelte</p>
						</div>
					</div>

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