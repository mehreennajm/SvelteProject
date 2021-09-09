<script>
    let activeTab = TabOne;
</script>
<button class="btn btn-primary" on:click={ () => (activeTab = TabOne)}> {tabOne} 
</button>
	<button class="btn btn-warning" on:click={ () => (activeTab = TabTwo)}> {tabTwo} </button>
	<button class="btn btn-info" on:click={ () => (activeTab = TabThree)}> {tabThree} </button>

	<svelte:component this={activeTab}></svelte:component>