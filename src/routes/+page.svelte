<script lang="ts">
  import type { Tooltip } from 'bootstrap';
  import { onMount } from 'svelte';
  import './main.scss';

  let bootstrap: typeof import('bootstrap');

  // enable Bootstrap tooltips
  onMount(async () => {
    bootstrap = await import('bootstrap');
  });

  const handleCopy = () => {
    // do something
    tooltip.show();
    setTimeout(() => tooltip.hide(), 1000);
  };

  $: tooltip = bootstrap?.Tooltip.getOrCreateInstance('#tooltip') as Tooltip;
</script>

<button type="button" class="btn btn-primary">Hello, World!</button>

<button
  class="btn btn-block btn-warning"
  data-bs-placement="bottom"
  data-bs-toggle="tooltip"
  data-bs-trigger="manual"
  id="tooltip"
  on:click={handleCopy}
  title="Clicked Successfully!"
  type="button"
>
  Click!
</button>
