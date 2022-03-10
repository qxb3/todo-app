<script>
	import 'carbon-components-svelte/css/g100.css'

	import Header from './components/Header.svelte'
	import Main from './components/Main.svelte'

	let todoList = []
	todoList.push({
		id: 0,
		title: 'Grocery',
		description: 'Buy a milk'
	})
</script>

<Header bind:todoList />
<Main bind:todoList />
