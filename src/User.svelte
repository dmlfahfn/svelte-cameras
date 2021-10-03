<script>

    export let user = {};

    const onClick = (e) => {
        e.preventDefault();
        console.log(e.target);
    }
    
</script>

<main>
    <li on:click={onClick}>{user.username}</li>
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