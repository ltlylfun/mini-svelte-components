<script>
  export let items;
  
  let openIndex = null;
  
  function toggleItem(index) {
    openIndex = openIndex === index ? null : index;
  }
</script>

<div>
  {#each items as item, idx}
    <div>
      <button
        type="button"
        style="cursor: pointer; font-weight: bold"
        on:click={() => toggleItem(idx)}
      >
        {item.title}
      </button>
      {#if openIndex === idx}
        <div>{@html item.content}</div>
      {/if}
    </div>
  {/each}
</div>
