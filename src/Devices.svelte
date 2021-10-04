<script>
    import {onMount} from "svelte";
    export let site;
    let devices = [];

    onMount(() => {
            fetch("http://localhost:3000/devices")
            .then(res => res.json())
            .then(data => {
                console.log(data)
                devices = data.filter(d => d.site_id == site.id)
            });
        });

</script>

<main>
    {#each devices as device}
        <div> Device name:  {device.title}, Device description: {device.description}</div>
    {:else}
        <div>Loading Devices</div>
    {/each}
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