<script>
import {onMount} from "svelte";

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

</main>

<style>

</style>