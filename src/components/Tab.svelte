<script>
	import { tabsKey } from './TabControl.svelte';
	import { getContext, onMount } from 'svelte';

	export let id;
	export let isTitle;
	export let isContent;
	
	const { selectedTab, tabs } = getContext(tabsKey);
	$tabs = $tabs.some(t => t == id)
		? $tabs
		: [...$tabs, id];
	
	$: isSelected = id == $selectedTab;
</script>


{#if isTitle}
	<button type="button" class="btn btn-primary"
					class:selected={isSelected}
					on:click={() => $selectedTab = id}>
		<slot name="title"/>
	</button>
{/if}

{#if isContent && isSelected}
	<slot/>
{/if}