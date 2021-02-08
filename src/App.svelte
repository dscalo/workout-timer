<script>
	import Main from './pages/main.svelte'
	import Timer from './pages/timer.svelte'

	let currentPage = {component: Timer, props: {}}

	const navigate = (page, props) => {
		switch(page.toLowerCase()) {
			case 'main':
				currentPage = {component: Main, props}
				break
			case 'timer':
				currentPage = {component: Timer, props}
				break
			default:
				currentPage = { component: Main, props: {} }
		}
	}
	
</script>

<main>
	<svelte:component this={currentPage.component} navigate={navigate} />
</main>

<style>
	
</style>