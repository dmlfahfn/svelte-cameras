<script>
    export let username = "";
    export let password = "";

    $: console.log("username", username)

    const onSubmit = (e) => {
        e.preventDefault();
        console.log("formsubmit", e.target.password.value);
    }

</script>

<form on:submit={onSubmit}>
    <input type ="text" id="username" bind:value={username}/>
    <input type ="password" id="password" bind:value={password}/>
    <button>Log In</button>
</form>

<style>

</style>