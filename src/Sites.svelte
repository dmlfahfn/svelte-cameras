<script>
    import {onMount} from "svelte";
    export let user;
    let sites = [];

    onMount(() => {
        console.log(user.username);
        fetch("http://localhost:3000/sites")
        .then(res => res.json())
        .then(data => {
            console.log(data)
            sites = data.filter(s => s.owner == user.username)
        });
    });

</script>

<main>
    
    {#each sites as site}
        <div>{site.title}</div>
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

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>