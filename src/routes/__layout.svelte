<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
</script>

<Header />

<main>
	<slot />
</main>

<footer>
	<p>
		Made by <a class="definitelymaybe" href="https://definitelymaybe.github.io/">DefinitelyMaybe</a>
		with <a class="sveltekit" href="https://kit.svelte.dev">svelte.kit</a>
		and <a class="netlify" href="https://www.netlify.com">netlify</a>
	</p>
	<p>
		It remixes a <a class="simon" href="https://github.com/simondevyoutube/Quick_3D_MMORPG">project</a>
		by <a class="simon" href="https://twitter.com/iced_coffee_dev">simondev</a>
	</p>
</footer>

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 0em;
	}

	footer a {
		font-weight: bold;
	}

	footer p {
		margin: 0;
		color: aliceblue;
	}

	a.definitelymaybe {
		color: rgb(58, 133, 160);
	}

	a.netlify {
		color: #139CAB
	}

	a.sveltekit {
		color: #ff3e00;
	}

	a.simon {
		color: rgb(58, 133, 160);
	}

	/* @media (min-width: 480px) {
		footer {
			padding: 0;
		}
	} */
</style>
