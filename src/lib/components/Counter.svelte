<script>
  export let initial = 0;
  
  let count = initial;
  
  $: count = initial;
</script>

<div>
  <button on:click={() => count--}>-</button>
  <span style="margin: 0 8px">{count}</span>
  <button on:click={() => count++}>+</button>
</div>
