<script>
	import { browser } from "$app/environment";

	import PocketBase, { cookieParse } from "pocketbase";

	const pb = new PocketBase("https://pb.bako.hackclub.app");

	const state = {
		email: "",
		password: "",
	};

	async function attmptSignin() {
		try {
			const authData = await pb
				.collection("BakoAUTH_Users")
				.authWithPassword(state.email, state.password);
			validateLogin();
		} catch (e) {
			console.log(e);
			alert("error occured: ", e);
		}
	}

	async function validateLogin() {
		if (pb.authStore.isValid) {
			pb.authStore.clear();
			document.cookie = "loggedin=true6988888934567";
			alert("logged in, redirecting now!");
			window.location.href = "/apps";
		} else {
			alert("try again :3");
		}
	}
</script>

<svelte:head>
	<title>Login to BakoAUTH!</title>
</svelte:head>

<section>
	<h1>Sign in to BakoAUTH!</h1>
	<p>
		reminder, your email is your login, your username is for when you contact us
		to do a password reset :3
	</p>
	<br />
	<span>Email: </span><input type="email" bind:value={state.email} required />
	<br />
	<span>Password: </span><input
		type="password"
		bind:value={state.password}
		required
	/>
	<br />
	<button
		on:click={() => {
			attmptSignin();
		}}>log in.</button
	>
</section>

<style>
</style>
