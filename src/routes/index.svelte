<!-- script section -->
<script>
	import { todos } from '$lib/store/store';
	import Modal from '$lib/components/Modal.svelte';
	import { v4 as uuidv4 } from 'uuid';

	let todo = '';
	let modal;

	const addTodo = (e) => {
		e.preventDefault();
		todos.update((todos) => {
            return [todo, ...todos];
                
		});
		todo = '';

	};
</script>

<section class="container">
	<h1>Ready to code and enjoy!!</h1>
	<form>
		<input action="text" placeholder="write here" bind:value={todo} required/>
		<button
			on:click={addTodo}
			on:click={() => modal.toogle()}
			type="submit"
			class="btn btn-secondary btn-lg"
		>
			add todo
		</button>
	</form>
	<Modal bind:this={modal}>
        <h2>🎉 Bravo! 🍾</h2>
        <p class="item"><strong>"{$todos[0]}"</strong> <br>has been added to your Todo List</p>
        <a href="/todolist"><button on:click={() => modal.toogle()} class="btn btn-secondary btn-lg btn-width" >See your list</button></a>
    </Modal>
</section>

<style lang="scss">
	@import '../vars.scss';

	.container {
		padding: $pXL 0;
		height: 100%;

		display: flex;
		flex-direction: column;
		align-items: center;
	}

	h1 {
		color: $font-color;
		margin-bottom: $mXL;
	}

	form {
		width: 50%;
		height: 200px;
		background-color: $bg-color;
		padding: $pM;
		@include flexColumn;
		border-radius: $bor-rad;
	}

    .btn-width {
        width: fit-content;
    }
	.item {
		text-align: center;
	}
</style>
