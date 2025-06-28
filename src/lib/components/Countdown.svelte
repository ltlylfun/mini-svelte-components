<script>
  import { onDestroy } from 'svelte';
  
  export let seconds;
  
  let time = seconds;
  let timer;
  
  $: {
    time = seconds;
    startCountdown();
  }
  
  function startCountdown() {
    if (timer) clearTimeout(timer);
    if (time === 0) return;
    
    timer = setTimeout(() => {
      time = time - 1;
      startCountdown();
    }, 1000);
  }
  
  onDestroy(() => {
    if (timer) clearTimeout(timer);
  });
</script>

<span>{time}</span>
