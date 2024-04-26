<script>
	import { browser } from "$app/environment";
	
	import PocketBase from "pocketbase";

	const pb = new PocketBase("https://pb.bako.hackclub.app");

	const state = {
		username: "",
		email: "",
		password: "",
	};

	async function attmptSignup() {
		try {
			const record = await pb.collection("BakoAUTH_Users").create({
				username: state.username,
				email: state.email,
				password: state.password,
				passwordConfirm: state.password,
			});
			sendVerificationEmail();
		} catch (e) {
			console.log("uhoh, error: " + e);
		}
	}

	async function sendVerificationEmail() {
		await pb.collection("BakoAUTH_Users").requestVerification(state.email);
		alert("Check your email for an email from bako@boombux.obl.ong!");
		window.location.href = "/signin";
	}
</script>

<svelte:head>
	<title>Sign Up for BakoAUTH!</title>
</svelte:head>

<section>
	<h1>Sign Up for BakoAUTH!</h1>
	<span>Username: </span><input
		type="text"
		bind:value={state.username}
		required
	/>
	<br />
	<span>Email: </span><input type="email" bind:value={state.email} required />
	<br />
	<span>Password: </span><input
		type="password"
		name="Pass"
		bind:value={state.password}
		required
	/>
	<br />
	<button
		on:click={() => {
			attmptSignup();
		}}>Sign up!</button
	>
</section>

<style>
</style>
