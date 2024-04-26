<script>
	import { browser } from "$app/environment";
</script>

<svelte:head>
	<title>BakoAuth-Home</title>
	<meta
		name="description"
		content="BakoAUTH - Get Access to iusebako's Services!"
	/>
</svelte:head>

<section>
	<h1>Welcome to BakoAUTH!</h1>
	<p>Get access to Bako's Services.</p>
	<a href="/signup"><button>Sign up for an account!</button></a>
	<a href="/signin"><button>Already have an account? Click me!</button></a>
	<a href="/apps"
		><button>Click me if you've logged in on this device.</button></a
	>
</section>

<style>
</style>
