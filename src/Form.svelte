<script>
    import { onMount } from "svelte";
    import Sites from "./Sites.svelte"
    let username = "";
    let password = "";
    let users = [];
    let user = null;

    onMount(() => {
        fetch("http://localhost:3000/users")
        .then(res => res.json())
        .then(data => {
            console.log(data)
            users = data
        });
    });

    const onSubmit = (e) => {
        e.preventDefault();
        user = users.filter(u => u.username == username && u.password == password)[0]
    };

</script>

<main>
    {#if !user}
    <form on:submit={onSubmit}>
        <input type ="text" id="username" bind:value={username}/>
        <input type ="password" id="password" bind:value={password}/>
        <button>Log In</button>
    </form>
    {/if}

    {#if user }
        <Sites {...{user}}/>
    {:else if user === undefined}
        <p>Are you sure you have the right username or password?</p>
    {/if}

</main>

<style>
main {
	text-align: center;
	padding: 10px;
	max-width: 448px;
	margin: 10px;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>