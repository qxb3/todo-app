<script>
	import { ClickableTile } from 'carbon-components-svelte'
	import TodoModal from './TodoModal.svelte'

	export let todoList

	let openTodoModal = false
	let openedTodo = {}

	const openTodo = (todo) => {
		openTodoModal = true
		openedTodo = todo
	}
</script>

<TodoModal
	bind:openTodoModal
	bind:todoList
	bind:todo={openedTodo}
/>

<main>
	{#each todoList as todo}
		<div class='tile-container'>
			<ClickableTile lighten on:click={() => openTodo(todo)}>
				<div class='tile-insides'>
					<h3 class='overflow'>{todo.title}</h3>
					<p class='overflow'>{todo.description}</p>
				</div>
			</ClickableTile>
		</div>
	{/each}
</main>

<style>
	main {
		margin: 16px;
	}

	.tile-container {
		padding-bottom: 12px;
	}

	.tile-insides {
		max-width: 100%;
		max-height: 80px;
		white-space: nowrap;
	}

	.overflow {
		overflow: hidden;
		text-overflow: ellipsis;
	}
</style>
