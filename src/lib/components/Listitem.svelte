<!-- my scripts -->
<script>
	import { todos } from '$lib/store/store';

	const deleteItem = (id) => {
		console.log(id);

		let index = $todos.indexOf(id);

		$todos = $todos.remove(index);

		console.log($todos);
	};
</script>

<h2>List of my todos:</h2>
<ul>
	{#if $todos.length == 0}
		<p>there is no tasks to do</p>
	{:else}
		{#each $todos as item}
			<li>
				- {item}
				<span on:click={deleteItem(item)} class="garbage"><i class="fas fa-trash-alt" /></span>
			</li>
		{/each}
	{/if}
</ul>

<style lang="scss">
	@import '../../vars.scss';

	h2 {
		color: $white;
		text-align: center;
	}

	ul {
		background-color: $light-color;
		width: 80%;
		border-radius: calc($bor-rad * 2);
		margin: 5% auto;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	li {
		background-color: $white;
		width: 70%;
		list-style: none;
		font-size: 1.5rem;
		line-height: 2rem;

		display: flex;
		justify-content: space-between;

		padding: $pS $pL;
		margin: $mM 0;

		border-radius: $bor-rad;
	}

	.garbage {
		cursor: pointer;
		color: $red-color;
	}
</style>
