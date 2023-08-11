<script>
	import TodoCard from "./TodoCard.svelte";

	let cards = [
		{todo: 'Belajar HTML', list: 'Tasks'},
		{todo: 'Belajar CSS Framework Bulma', list: 'Tasks'},
		{todo: 'Belajar Javascript', list: 'Tasks'},
		{todo: 'Belajar Svelte', list: 'Tasks'},
	];

	let todo = "";

	function handlerAddCard() {
		// DOM element dari data cards tidak akan terupdate jika tidak menggunakan operator assigment "="
		// Misal cards.push() tampilan list card tidak akan ter update

		cards = [...cards, {todo, list: 'Tasks'}];
		todo = "";
	}

	function onInputEnter(e) {
		if(e.key == "Enter"){
			handlerAddCard();
		}
	}
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
					{#each cards as card}
						<TodoCard content={card.todo} />
					{/each}
					<input type="text" class="input is-primary mb-1" bind:value={todo} on:keydown={onInputEnter}/>
					<button on:click={handlerAddCard} class="button is-primary">Add Card</button>
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