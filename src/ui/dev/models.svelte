<script>
  import { newModelData } from "../../data/models/mod.js";

  export let selected;
  let data = [];
  const models = []

  $: if (selected) {
    data = []
    for (const key in newModelData?.[selected]) {
      const val = newModelData[selected][key];
      data.push({key, val});
    }
  }

  for (const name in newModelData) {
    models.push(name)
  }
</script>

<label for="">Model Picker</label>
<!-- <label for="">Model:</label> -->
<select bind:value="{selected}" on:change>
  {#each models as name}
    <option value="{name}">{name}</option>
  {/each}
</select>
  <!-- {#each data as pair}
    {#if typeof(pair.val) == "string"}
      <label for="">{pair.key}</label><input type="text" bind:value="{pair.val}"><br>
    {:else if typeof(pair.val) == "number"}
      <label for="">{pair.key}</label><input type="number" bind:value="{pair.val}"><br>
    {:else if typeof(pair.val) == "boolean"}
      <label for="">{pair.key}</label><input type="checkbox" bind:checked="{pair.val}"><br>
    {:else}
      <label for="">{pair.key}</label>{pair.val} <br>
    {/if}
  {/each}
  <button on:click="{() => {
    console.log("Lets add another variable");
  }}">+</button> -->

<style>
  select {
    width: 10%;
    pointer-events: all;
  }
</style>