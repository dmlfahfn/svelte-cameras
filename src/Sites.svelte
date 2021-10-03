<script>
import Site from "./Sites.svelte";
    export let sites = [];

    onMount(() => {
        fetch("http://localhost:3000/sites")
        .then(res => res.json())
        .then(data => {
            console.log(data)
            sites = data
        });
    })

</script>

<main>
    {#each sites as site}
        <Site {site} />
    {:else}
        <div>Hämtar Sites</div>
    {/each}
</main>

<style>
main {
		text-align: center;
		padding: 10px;
		max-width: 448px;
		margin: 10px;
        border: 1px solid #ff3e00;
    }
    li {
        list-style: none;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>