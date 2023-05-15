<script>
    import * as d3 from 'd3';
    import { onMount } from 'svelte';
	let user = { loggedIn: false };

	function toggle() {
		user.loggedIn = !user.loggedIn;
	}

    let cats = [
        { id: 1, name: 'chipchat', place: 'ozo'},
        { id: 2, name: 'Poupouss', place: 'rosoux'},
        { id: 3, name: 'Darla', place: 'Liège'},

    ];
</script>

<style>
button {
        padding: 10px;
        border-radius: 5px;
        color:black;
        background-color: aquamarine;
        border-color: aquamarine;
    }
</style>

{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{:else}
	<button on:click={toggle}>
		Log in
	</button>
{/if}

{#each cats as cat }
<p> {cat.name}</p>
{/each}