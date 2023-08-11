<script>
  import CardList from "./CardList.svelte";

	let taskCardsLocalStorage = JSON.parse(localStorage.getItem('taskCards'));
	let inProgressCardsLocalStorage = JSON.parse(localStorage.getItem('inProgressCards'));
	let doneCardsLocalStorage = JSON.parse(localStorage.getItem('doneCards'));

	let taskCards = taskCardsLocalStorage ? taskCardsLocalStorage : [];
	let inProgressCards = inProgressCardsLocalStorage ? inProgressCardsLocalStorage : [];
	let doneCards = doneCardsLocalStorage ? doneCardsLocalStorage : [];

	function handlerEventAddCard(event) {
		let data = event.detail;

		// DOM element dari data cards tidak akan terupdate jika tidak menggunakan operator assigment "="
        // Misal cards.push() tampilan list card tidak akan ter update
		if(data.listName == 'Task'){
			taskCards = [...taskCards, {todo : data.todo}];
			localStorage.setItem('taskCards', JSON.stringify(taskCards));

		}else if(data.listName == 'In Progress'){
			inProgressCards = [...inProgressCards, {todo : data.todo}];
			localStorage.setItem('inProgressCards', JSON.stringify(inProgressCards));

		}else if(data.listName == 'Done'){
			doneCards = [...doneCards, {todo : data.todo}];
			localStorage.setItem('doneCards', JSON.stringify(doneCards));

		}
		
	}

	function handlerEventDeleteCard(event) {
		let data = event.detail;

		if(data.listName == 'Task'){
			taskCards.splice(data.index, 1);
			taskCards = taskCards;
			localStorage.setItem('taskCards', JSON.stringify(taskCards));

		}else if(data.listName == 'In Progress'){
			inProgressCards.splice(data.index, 1);
			inProgressCards = inProgressCards;
			localStorage.setItem('inProgressCards', JSON.stringify(inProgressCards));

		}else if(data.listName == 'Done'){
			doneCards.splice(data.index, 1);
			doneCards = doneCards;
			localStorage.setItem('doneCards', JSON.stringify(doneCards));

		}
	}

	function handlerEventMoveRight(event) {
		let data = event.detail;

		if(data.listName == 'Task'){
			let cardToMove = taskCards.splice(data.index, 1);
			inProgressCards = [...inProgressCards, cardToMove[0]];
			taskCards = taskCards;

			localStorage.setItem('taskCards', JSON.stringify(taskCards));
			localStorage.setItem('inProgressCards', JSON.stringify(inProgressCards));

		}else if(data.listName == 'In Progress'){
			let cardToMove = inProgressCards.splice(data.index, 1);
			doneCards = [...doneCards, cardToMove[0]];
			inProgressCards = inProgressCards;

			localStorage.setItem('inProgressCards', JSON.stringify(inProgressCards));
			localStorage.setItem('doneCards', JSON.stringify(doneCards));

		}
	}

	function handlerEventMoveLeft(event) {
		let data = event.detail;

		if(data.listName == 'In Progress'){
			let cardToMove = inProgressCards.splice(data.index, 1);
			taskCards = [...taskCards, cardToMove[0]];
			inProgressCards = inProgressCards;

			localStorage.setItem('inProgressCards', JSON.stringify(inProgressCards));
			localStorage.setItem('taskCards', JSON.stringify(taskCards));

		}else if(data.listName == 'Done'){
			let cardToMove = doneCards.splice(data.index, 1);
			inProgressCards = [...inProgressCards, cardToMove[0]];
			doneCards = doneCards;

			localStorage.setItem('doneCards', JSON.stringify(doneCards));
			localStorage.setItem('inProgressCards', JSON.stringify(inProgressCards));
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