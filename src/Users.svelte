<script>
import { onMount } from "svelte";
import User from "./User.svelte";
import Form from "./Form.svelte";


    export let users = [];

    onMount(() => {
        fetch("http://localhost:3000/users")
        .then(res => res.json())
        .then(data => {
            console.log(data)
            users = data
        });
    });

</script>

<main>
    <Form />
    {#each users as user}
        <User {user} />
    {:else}
        <div>Hämtar Owner</div>
    {/each}
</main>

<style>
    
</style>