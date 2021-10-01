<script>
import { onMount } from "svelte";
import User from "./User.svelte";


    export let users = [];

    onMount(() => {
        fetch("http://localhost:3000/sites")
        .then(res => res.json())
        .then(data => {
            console.log(data)
            users = data
        });
    })

</script>

<main>
    {#each users as user}
        <User {user} />
    {:else}
        <div>Hämtar Owner</div>
    {/each}
</main>

<style>
    
</style>