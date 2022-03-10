<script>
	import { Modal, Form, TextInput } from 'carbon-components-svelte'

	export let openNewTodoModal
	export let submitTodo

	export let todoTitle
	export let todoDescription
</script>

<Modal
	bind:open={openNewTodoModal}
	modalHeading='Add new todo'
	primaryButtonText='Save'
	secondaryButtonText='Cancel'
	on:click:button--secondary={() => (openNewTodoModal = false)}
	on:submit={() => {
		openNewTodoModal = false
		submitTodo()
	}}
>
	<Form>
		<TextInput bind:value={todoTitle} labelText='Title' placeholder='Do the math assignment' required />
		<TextInput bind:value={todoDescription} labelText='Description' placeholder='What even is 1+1?' required />
	</Form>
</Modal>
