<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let name;
  export let points;
  let showControls = false;
</script>

<style>
  .controls {
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>

<div class="card">
  <h1>
    {name}
    <button class="btn btn-sm" on:click={() => (showControls = !showControls)}>
      {#if showControls}-{:else}+{/if}
    </button>
    <button
      class="btn btn-danger btn-sm"
      on:click={() => dispatch('removePlayer', name)}>
      x
    </button>
  </h1>
  <h4>Points: {points}</h4>
  {#if showControls}
    <div class="controls">
      <button class="btn" on:click={() => points--}>-1</button>
      <button class="btn" on:click={() => points++}>+1</button>
      <input type="number" bind:value={points} />
    </div>
  {/if}
</div>
