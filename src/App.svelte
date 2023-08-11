<script>
  import CardList from "./CardList.svelte";


	let taskCards = [
		{todo: 'Belajar HTML', list: 'Tasks'},
		{todo: 'Belajar CSS Framework Bulma', list: 'Tasks'},
		{todo: 'Belajar Javascript', list: 'Tasks'},
		{todo: 'Belajar Svelte', list: 'Tasks'},
	];

	let inProgressCards = [];
	let doneCards = [];

</script>

<div class="container is-fullhd is-fluid">
	<h1 class="is-size-3">TODO APP</h1>

	<div class="columns">
		<CardList cards={taskCards} listName={'Task'} />
		<CardList cards={inProgressCards} listName={'In Progress'} />
		<CardList cards={doneCards} listName={'Done'} />
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