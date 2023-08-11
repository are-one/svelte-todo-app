<script>
    import { createEventDispatcher } from "svelte";
    import TodoCard from "./TodoCard.svelte";

    // Mendefinisikan props
    export let cards, listName;

    const dispatch = createEventDispatcher();

    let todo = "";
    function handlerAddCard() {        
        // Mengirim data melalui event dispatcher
        dispatch('addCard',{todo, listName});
        todo = "";
    }

    function onInputEnter(e) {
        if(e.key == "Enter"){
            handlerAddCard();
        }
    }

    function handlerEventDeleteCard(event) {
        let data = event.detail;
        dispatch('deleteCard', { index: data.index, listName});
    }
</script>

<style></style>

<div class="column is-4">
    <div class="card has-background-light">
        <div class="card-header">
            <div class="card-header-title">{listName}</div>
        </div>
        <div class="card-content">
            {#each cards as card, index}
                <TodoCard content={card.todo} listName={listName} index={index} on:deleteCard={handlerEventDeleteCard}/>
            {/each}
            <input type="text" class="input is-primary mb-1" bind:value={todo} on:keydown={onInputEnter}/>
            <button on:click={handlerAddCard} class="button is-primary">Add Card</button>
        </div>
    </div>
</div>