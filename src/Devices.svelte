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
        <div>{device.title}</div>
    {:else}
        <div>Loading Devices</div>
    {/each}
</main>

<style>

</style>