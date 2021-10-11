<script context="module">
	export const prerender = true;
</script>

<script>
  import { onMount, onDestroy } from "svelte";
  import { World } from "../worlds/simonsWorld.js";
  // import Chat from "../ui/game/chat.svelte";
  import HUD from "../ui/game/hud.svelte";
  import Menu from "../ui/game/menu.svelte";
  // import Simplex from "../ui/dev/simplex.svelte";
  // import Points from "../ui/dev/poisson.svelte";


  let world;
  let chat;

  // TODO-DefinitelyMaybe: focus lost could be a good, stop/start the clock/loop signal
  let focused = false

  // let showHUD = true
  // let showMenu = true;
  // let showChat = true

  function test() {
    console.log(world);
  }

  function test2() {
    console.log(world.entities.player);
  }

  onMount(() => {
    world = new World()
    // showHUD = true
    world.resize()
  })
  
  onDestroy(() => {
    if (world) {
      const workers = world.terrain.builder.workers
      workers.forEach(worker => {
        worker.terminate()
      }); 
    }
  })
</script>

<svelte:window on:blur="{() => {
    focused = false
    world.stop()}}"
  on:focus="{() => {
    focused = true
    world.start()}}"
  on:resize="{() => {world.resize()}}"></svelte:window>
<svelte:body on:keyup="{(event) => {world.input.handleKeyup(event)}}"
  on:keydown="{(event) => {world.input.handleKeydown(event)}}"
  on:pointerdown="{(event)=>{world.input.handlePointerdown(event)}}"
  on:pointerup="{(event)=>{world.input.handlePointerup(event)}}"></svelte:body>

<canvas id="game"></canvas>
<!-- <Chat bind:this="{chat}" on:send="{(e)=> {
  // TODO-DefinitelyMaybe: Send author info as well
  const {text} = e.detail
  world.network.websocket.emit("chat.message", text)
}}"></Chat> -->
<HUD></HUD>
<Menu on:test="{test}" on:test2="{test2}"></Menu>
<details>
  <summary>Help?</summary>
  Use `wasd` keys to move around. <br>
  Unfortunately physics doesn't know about the terrain <br>
  and there's no multiplayer. <br>
  Your more than welcome to remix this <a href="https://github.com/DefinitelyMaybe/glowing-octo-train/blob/main/LICENSE">(It's MIT lincensed)</a><br>
  If the terrain isn't textured, give the page a quick refresh.
  <!-- <Simplex></Simplex>
  <Points></Points> -->
</details>

<style>
  :global(body) {
    width: 100%;
    height: 100%;
    background: black;
    color: white;
    margin: 0;
    overflow: hidden;
    font-size: x-large;
    pointer-events: none;
  }
  canvas {
    position: absolute;
    top: 0px;
    left: 0px;
    z-index: -1;
    pointer-events: all;
  }
  details {
    pointer-events: all;
  }
</style>