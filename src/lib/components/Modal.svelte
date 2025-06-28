<script>
  export let open = false;
  export let onClose = () => {};
</script>

{#if open}
  <div>
    <div>
      <slot></slot>
      <button on:click={onClose}>关闭</button>
    </div>
  </div>
{/if}
