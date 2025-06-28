<script>
  import { onMount, onDestroy } from 'svelte';
  
  export let message;
  export let duration = 2000;
  export let onClose = () => {};
  
  let timer;
  
  function startTimer() {
    if (!message) return;
    if (timer) clearTimeout(timer);
    
    timer = setTimeout(() => {
      onClose();
    }, duration);
  }
  
  $: if (message) {
    startTimer();
  }
  
  onDestroy(() => {
    if (timer) clearTimeout(timer);
  });
</script>

{#if message}
  <div>{message}</div>
{/if}
