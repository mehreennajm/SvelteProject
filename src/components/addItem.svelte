<script>
  import {
    createEventDispatcher
  } from 'svelte'
  const dispatch = createEventDispatcher();
  let ListItem = [{
    item: ""
  }];
  const OnSubmit = e => {
    e.preventDefault();
    dispatch("item", ListItem);
    ListItem = {
      item: ""
    }
  }
</script>
<h5>My ToDo List </h5>
<form on:submit={OnSubmit}>
  <div class="file-field input-field">
    <input type="submit" value="Add new item +" class="btn">
    <div class="file-path-wrapper">
      <input type="text" placeholder="Type the Item you want to do " bind:value={ListItem.item} required="required" />
    </div>
</form>
<style>
  h5 {
    text-align: left;
    color: rgb(172, 168, 167);
  }
</style>