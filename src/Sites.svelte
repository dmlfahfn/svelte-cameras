<script>
    import {onMount} from "svelte";
    import Devices from "./Devices.svelte";
    export let user;
    let sites = [];
    let site = null;

    onMount(() => {
        fetch("http://localhost:3000/sites")
        .then(res => res.json())
        .then(data => {
            console.log(data)
            sites = data.filter(s => s.owner == user.username)
        });
    });

    const onClick = (e) => {
        e.preventDefault();
        site = sites.filter(s => s.id)
    };

</script>

<main>
    {#if !site}
        {#each sites as _site}
            <div on:click={() => site = _site}>{_site.title }</div>
        {:else}
            <div>Loading Sites</div>
        {/each}
    {/if}

    {#if site }
        <Devices {...{site}}/>
    {:else if site === undefined}
        <p>Please click on the sites to view the devices!</p>
    {/if}
</main>

<style>
main {
	text-align: center;
	padding: 10px;
	max-width: 448px;
	margin: 10px;
    }
    
main div{
    border:1px solid #ff3e00;
    padding: 10px;
    margin: 10px;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>