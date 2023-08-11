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

	function handlerEventAddCard(event) {
		let data = event.detail;

		// DOM element dari data cards tidak akan terupdate jika tidak menggunakan operator assigment "="
        // Misal cards.push() tampilan list card tidak akan ter update
		if(data.listName == 'Task'){
			taskCards = [...taskCards, {todo : data.todo}];
		}else if(data.listName == 'In Progress'){
			inProgressCards = [...inProgressCards, {todo : data.todo}];
			
		}else if(data.listName == 'Done'){
			doneCards = [...doneCards, {todo : data.todo}];
		}
		
	}

</script>

<div class="container is-fullhd is-fluid">
	<h1 class="is-size-3">TODO APP</h1>

	<div class="columns">
		<CardList 
			cards={taskCards}
			listName={'Task'}
			on:addCard={handlerEventAddCard}
			/>
		<CardList 
			cards={inProgressCards} 
			listName={'In Progress'}  
			on:addCard={handlerEventAddCard}
			/>
		<CardList 
			cards={doneCards}
			listName={'Done'}  
			on:addCard={handlerEventAddCard}
			/>
	</div>
</div>

<!-- Cara 2 Mengintegrasikan css framework Bulma -->
<svelte:head>
	<link rel="stylesheet" href="/bulma.min.css" />
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css" integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
</svelte:head>

<style>
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

</style>