<script>
  export let tabs;
  
  let activeIndex = 0;
</script>

<div>
  <div>
    {#each tabs as tab, idx}
      <button on:click={() => activeIndex = idx}>
        {tab.label}
      </button>
    {/each}
  </div>
  <div>
    {@html tabs[activeIndex].content}
  </div>
</div>
