<script>
	import 'carbon-components-svelte/css/g100.css'
	import { Button, Modal, Form, TextInput, ClickableTile, Checkbox } from 'carbon-components-svelte'

	//Add new todo stuff
	let todoTitle = ''
	let todoDescription = ''

	let todos = []
	todos.push({
		title: 'Grocery',
		description: 'Buy a milk'
	})

	let open = false
	const submit = () => {
		open = false

		todos.push({
			title: todoTitle,
			description: todoDescription
		})
		todos = todos

		todoTitle = ''
		todoDescription = ''
	}
</script>

<main>
	<header>
		<Button kind='secondary' on:click={() => open = true}>Add new</Button>
	</header>

	<div class='main'>
		{#each todos as todo}
			<ClickableTile light>
				<Checkbox />
				<div>
					<h3>{todo.title}</h3>
					<p>{todo.description}</p>
				</div>
			</ClickableTile>
		{/each}
	</div>
</main>

<Modal
  bind:open
  modalHeading='Add new todo'
  primaryButtonText='Save'
  secondaryButtonText='Cancel'
  on:click:button--secondary={() => (open = false)}
  on:submit={submit}
>
	<Form>
		<TextInput bind:value={todoTitle} labelText='Title' placeholder='Do the math assignment' required />
		<TextInput bind:value={todoDescription} labelText='Description' placeholder='What even is 1+1?' required />
	</Form>
</Modal>

<style>
	main {
		margin: 16px;
	}

	header {
		display: flex;
		justify-content: end;
	}

	.main * {
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin: 8px;
		padding: 8px;
	}

	.main * div h3 {
		font-size: 2rem;
		background-color: #cccc;
	}
</style>
