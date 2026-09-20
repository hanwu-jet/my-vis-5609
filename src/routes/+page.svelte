<script>
  import { asset } from '$app/paths';

  let maxClick = $state(5);
  let cnt = $state(5);

  function onClick() {
    if (cnt > 0) {
      cnt -= 1;
    }
  }
</script>

<h1>Han Wu's VIS Site</h1>

<img
  width="200"
  src={asset('/favorite.jpg')}
  alt="My favorite"
/>

<div>
  You can click up to

  <select
    bind:value={maxClick}
    onchange={(event) => {
      maxClick = Number(event.currentTarget.value);
      cnt = maxClick;
    }}
  >
    {#each [5,4,3,2,1] as optionNum}
      <option value={optionNum}>
        {optionNum}
      </option>
    {/each}
  </select>

  times
</div>

<button onclick={onClick}>Click Me</button>

{#if cnt > 0}
  <p id="info">Remaining Number of Clicks: {cnt}</p>
{:else}
  <p>No more clicks allowed</p>
{/if}

<style>
  :global(body) {
    font-family: Arial, Helvetica, sans-serif;
  }

  button {
    background-color: #44aa66;
    color: white;
    font-size: xx-large;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    border-radius: 5px;
  }
</style>