<script>
  import { createEventDispatcher } from "svelte";
  import { slide } from "svelte/transition"; // fade, fly, slide
  

    export let content, listName, index;
    const dispatch = createEventDispatcher();

    function handlerDeleteCard(){
        dispatch('deleteCard', {index});
    }

    function handlerMoveRight() {
        dispatch('moveRight', {index});
    }

    function handlerMoveLeft() {
        dispatch('moveLeft', {index});
    }
    
</script>

<div class="card mb-3 has-background-primary-light" transition:slide>
    <div class="card-content">
        <div class="columns is-centered">
            {#if listName != "Task"}
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <div class="column is-1 is-flex is-justify-content-center" on:click={handlerMoveLeft}>
                    <span class="icon has-text-primary">
                        <i class="fas fa-chevron-left"></i>
                    </span>
                </div>
            {:else}
                <div class="column is-1 is-flex is-justify-content-center">
                </div>
            {/if}
            <div class="column is-9">
                <p class="has-text-primary-dark">{content}</p>
            </div>
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <div class="column is-1 is-flex is-justify-content-center" on:click={handlerDeleteCard}>
                <span class="icon has-text-danger">
                    <i class="fas fa-trash"></i>
                </span>
            </div>
            {#if listName != 'Done'}
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <div class="column is-1 is-flex is-justify-content-center" on:click={handlerMoveRight}>
                    <span class="icon has-text-primary">
                        <i class="fas fa-chevron-right"></i>
                    </span>
                </div>
            {:else}
                <div class="column is-1 is-flex is-justify-content-center">
                </div>
            {/if}
        </div>
    </div>
</div>