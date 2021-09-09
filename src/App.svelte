<script>
  import TabControl from './components/TabControl.svelte';
  import Tab from './components/Tab.svelte';
  import {
    onMount
  } from "svelte";
  let date = new Date();
  $: hour = date.getHours();
  $: minutes = date.getMinutes();
  $: seconds = date.getSeconds();
  onMount(() => {
    const interval = setInterval(() => {
      date = new Date();
    }, 1000);
  });
  import FullCalendar from "svelte-fullcalendar";
  import dayGridPlugin from "@fullcalendar/daygrid";
  let options = {
    initialView: "dayGridMonth",
    plugins: [dayGridPlugin]
  };
  import ToDoItems from "./components/toDo.svelte";
  import AddItem from "./components/addItem.svelte";
  let ListItems = [{
    item: "Meeting with Rodrigue at 3:00 PM"
  }, {
    item: "Design and Development of new project"
  }, {
    item: "Learning Svelte.js Compiler"
  }];
  const addToDoItem = (e) => {
    const newItem = e.detail;
    ListItems = [...ListItems, newItem];
  };
  const removeItem = (e) => {
    ListItems = ListItems.filter((Item) => Item.item !== e.detail);
  };
</script>
<main>
  <TabControl let:isTitle let:isContent>
    <Tab id="0" {isTitle} {isContent}>
      <span slot="title">Current Time</span>
      <div class="row">
        <div class="col s12 m4 offset-m4">
          <i class="large material-icons">access_time</i>
          <h1>Current Time </h1>
          <h3>{hour} : {minutes} : {seconds} </h3>
        </div>
      </div>
    </Tab>
    <Tab id="1" {isTitle} {isContent}>
      <span slot="title">Calender</span>
      <div class="row">
        <div class="col s12 m5 offset-m4">
          <FullCalendar {options} />
        </div>
      </div>
    </Tab>
    <Tab id="2" {isTitle} {isContent}>
      <span slot="title">ToDo List</span>
      <div class="container">
        <AddItem on:item="{addToDoItem}" /> {#if ListItems.length === 0}
    
				<p class="card-panel orange lighten-1">No Items to list</p>
    {:else} {#each ListItems as Item}

    
				<ToDoItems Item="{Item.item}" on:removeitem="{removeItem}" />

    {/each} {/if}

			</div>
		</Tab>
	</TabControl>
</main>
<style>
main {
	text-align: center;
	max-width: 1000px;
	margin: 0 auto;
}

@media (min-width: 360px) {
	main {
		max-width: none;
	}

	.row .col.m4 {
		background-color:#d1e6e3  !important;
		border-radius:4%;
	}

	h1 {
		color: #1b4343;
		font-style: italic;
	}
}
</style>