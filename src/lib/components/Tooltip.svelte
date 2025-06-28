<script>
  export let text;
  
  let visible = false;
</script>

<span
  role="tooltip"
  on:mouseenter={() => visible = true}
  on:mouseleave={() => visible = false}
>
  <slot></slot>
  {#if visible}
    <span>{text}</span>
  {/if}
</span>
