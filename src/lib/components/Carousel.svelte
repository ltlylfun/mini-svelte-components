<script>
  import { onDestroy } from 'svelte';
  
  const images = [
    import.meta.env.BASE_URL + "react.svg",
    import.meta.env.BASE_URL + "svelte.svg", 
    import.meta.env.BASE_URL + "vuedotjs.svg"
  ];
  
  let index = 0;
  let timer;
  
  function startAutoplay() {
    timer = setInterval(() => {
      index = index === images.length - 1 ? 0 : index + 1;
    }, 5000);
  }
  
  function prev() {
    index = index === 0 ? images.length - 1 : index - 1;
  }
  
  function next() {
    index = index === images.length - 1 ? 0 : index + 1;
  }
  
  startAutoplay();
  
  onDestroy(() => {
    if (timer) clearInterval(timer);
  });
</script>

<div>
  <button on:click={prev}>上一张</button>
  <img
    src={images[index]}
    alt="carousel"
    style="width: 200px; height: 200px; margin: 0 20px"
  />
  <button on:click={next}>下一张</button>
</div>
