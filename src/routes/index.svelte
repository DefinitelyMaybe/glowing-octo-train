<script context="module">
	export const prerender = true;
</script>

<svelte:head>
	<title>The Remix</title>
</svelte:head>

<section class="login-screen">
	<div class="login-screen-layout window">
		Enter:
		<a sveltekit:prefetch href="/simonsWorld">Simon's World</a>
		<a sveltekit:prefetch href="/entityViewer">Entity Viewer</a>
	</div>
</section>

<style>
	:global(body) {
    width: 100%;
    height: 100%;
    background: #000000;
    color: white;
    margin: 0;
    overflow: hidden;
    font-size: x-large;
  }

	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	.login-screen {
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    font-family: serif;
    background-image: url("./resources/background-3.png");
		background-repeat: no-repeat;
		background-size: contain;
		background-position: left;
  }
  
  .login-screen-layout {
    display: flex;
    height: 100%;
    width: 100%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .login-screen-layout.window {
    height: 100px;
    width: 30%;
    border-radius: 5px;
    border-color: black;
    border-style: solid;
    background: rgba(0, 0, 0, 0.75);
  }
</style>
