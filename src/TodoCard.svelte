<script>
  import { createEventDispatcher } from "svelte";

    export let content, listName, index;
    const dispatch = createEventDispatcher();

    function handlerDeleteCard(){
        dispatch('deleteCard', {index});
    }

</script>

<div class="card mb-3 has-background-primary-light">
    <div class="card-content">
        <div class="columns is-centered">
            <div class="column is-1 is-flex is-justify-content-center">
                {#if listName != "Task"}
                <span class="icon has-text-primary">
                    <i class="fas fa-chevron-left"></i>
                </span>
                {/if}
            </div>
            <div class="column is-9">
                <p class="has-text-primary-dark">{content}</p>
            </div>
            <div class="column is-1 is-flex is-justify-content-center" on:click={handlerDeleteCard}>
                <span class="icon has-text-danger">
                    <i class="fas fa-trash"></i>
                </span>
            </div>
            <div class="column is-1 is-flex is-justify-content-center">
                {#if listName != 'Done'}
                <span class="icon has-text-primary">
                    <i class="fas fa-chevron-right"></i>
                </span>
                {/if}
            </div>
        </div>
    </div>
</div>