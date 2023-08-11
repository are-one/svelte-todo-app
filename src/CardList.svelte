<script>
    import TodoCard from "./TodoCard.svelte";

    // Mendefinisikan props
    export let cards, listName;

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

<style></style>

<div class="column is-4">
    <div class="card has-background-light">
        <div class="card-header">
            <div class="card-header-title">{listName}</div>
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