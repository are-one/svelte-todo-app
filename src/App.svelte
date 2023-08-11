<script>
  import CardList from "./CardList.svelte";


	let taskCards = [];
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

	function handlerEventDeleteCard(event) {
		let data = event.detail;

		if(data.listName == 'Task'){
			taskCards.splice(data.index, 1);
			taskCards = taskCards;

		}else if(data.listName == 'In Progress'){
			inProgressCards.splice(data.index, 1);
			inProgressCards = inProgressCards;

		}else if(data.listName == 'Done'){
			doneCards.splice(data.index, 1);
			doneCards = doneCards;
		}
	}

	function handlerEventMoveRight(event) {
		let data = event.detail;

		if(data.listName == 'Task'){
			let cardToMove = taskCards.splice(data.index, 1);
			inProgressCards = [...inProgressCards, cardToMove[0]];
			taskCards = taskCards;
		}else if(data.listName == 'In Progress'){
			let cardToMove = inProgressCards.splice(data.index, 1);
			doneCards = [...doneCards, cardToMove[0]];
			inProgressCards = inProgressCards;
		}
	}

	function handlerEventMoveLeft(event) {
		let data = event.detail;

		if(data.listName == 'In Progress'){
			let cardToMove = inProgressCards.splice(data.index, 1);
			taskCards = [...taskCards, cardToMove[0]];
			inProgressCards = inProgressCards;
		}else if(data.listName == 'Done'){
			let cardToMove = doneCards.splice(data.index, 1);
			inProgressCards = [...inProgressCards, cardToMove[0]];
			doneCards = doneCards;
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
			on:deleteCard={handlerEventDeleteCard}
			on:moveRight={handlerEventMoveRight}
			/>
		<CardList 
			cards={inProgressCards} 
			listName={'In Progress'}  
			on:addCard={handlerEventAddCard}
			on:deleteCard={handlerEventDeleteCard}
			on:moveRight={handlerEventMoveRight}
			on:moveLeft={handlerEventMoveLeft}
			/>
		<CardList 
			cards={doneCards}
			listName={'Done'}  
			on:addCard={handlerEventAddCard}
			on:deleteCard={handlerEventDeleteCard}
			on:moveLeft={handlerEventMoveLeft}
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