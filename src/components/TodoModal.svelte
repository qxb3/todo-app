<script>
	import { Modal } from 'carbon-components-svelte'

	export let todoList
	export let openTodoModal
	export let todo

	const onDelete = () => {
		openTodoModal = false
		todoList = todoList.filter((item) => item.title !== todo.title)
	}

	const onFinished = () => {
		openTodoModal = false
		todoList = todoList.filter((item) => item.title !== todo.title)
	}
</script>

<Modal
	bind:open={openTodoModal}
	modalHeading={todo.title}
	secondaryButtonText='Delete'
	primaryButtonText='Finished'
	on:click:button--secondary={onDelete}
	on:click:button--primary={onFinished}
>
	<p>{todo.description}</p>
</Modal>
