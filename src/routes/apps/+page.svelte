<script>
	import { browser } from "$app/environment";

	if (browser) {
		const cookie = document.cookie.match(/^\s*loggedin\s*=\s*([^;]+)/);

		if (cookie == null) {
			alert("NUH UH. GO LOG IN. >:3c");
			window.location.href = "/signin";
		} else {
			console.log("let them in");
		}
	}
</script>

<svelte:head>
	<title>Apps</title>
</svelte:head>

<section>
	<h2>Welcome back!</h2>
	<br />
	<h3>Apps:</h3>
	<a href="https://bako.hackclub.app">Placeholder</a>
</section>

<style>
</style>
