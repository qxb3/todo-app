<script>
	import { Button } from 'carbon-components-svelte'
	import NewTodoModal from './NewTodoModal.svelte'

	export let todoList

	let openNewTodoModal = false
	let todoTitle = ''
	let todoDescription = ''

	const submitTodo = () => {
		todoList.push({
			title: todoTitle,
			description: todoDescription
		})
		todoList = todoList

		todoTitle = ''
		todoDescription = ''
	}
</script>

<NewTodoModal
	bind:openNewTodoModal
	bind:todoTitle
	bind:todoDescription
	{submitTodo}
	/>

<header>
	<Button kind='secondary' on:click={() => openNewTodoModal = true}>New Todo</Button>
</header>

<style>
	header {
		display: flex;
		justify-content: end;
		margin: 16px;
	}
</style>
