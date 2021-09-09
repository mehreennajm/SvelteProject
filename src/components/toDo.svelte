<script>
  import {
    createEventDispatcher
  } from 'svelte'
  const dispatch = createEventDispatcher();
  export let Item;
  const DeleteItem = () => dispatch("removeitem", Item);
  let number = 0;
</script>
<main>
  <div class="row">
    <div class="col s12 m12">
      <div class="card-panel teal">
        <span class="white-text">{Item} <button class="btn-floating btn-sm waves-effect waves-light orange darken-4" on:click={DeleteItem}>
            <i class="material-icons">remove</i>
          </button>
        </span>
      </div>
    </div>
  </div>
</main>
<style>
  .card-panel {
    font-size: 1em;
    text-align: left;
  }

  .card-panel button {
    margin-left: 2%;
  }

  .teal {
    background-color: #73aea8 !important;
  }
</style>