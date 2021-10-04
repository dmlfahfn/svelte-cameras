<script>

    export let user = {};
    
</script>

<main>
    {user.username}
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