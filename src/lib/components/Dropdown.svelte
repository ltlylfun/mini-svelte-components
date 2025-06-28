<script>
  import { onMount } from 'svelte';
  
  export let options = [];
  export let value = null;
  export let onChange = (value) => {};
  export let placeholder = "请选择";
  
  let open = false;
  let dropdownRef;
  
  function handleClickOutside(event) {
    if (dropdownRef && !dropdownRef.contains(event.target)) {
      open = false;
    }
  }
  
  function selectOption(option) {
    onChange(option.value);
    open = false;
  }
  
  onMount(() => {
    document.addEventListener('mousedown', handleClickOutside);
    return () => {
      document.removeEventListener('mousedown', handleClickOutside);
    };
  });
  
  $: selectedOption = options.find(o => o.value === value);
</script>

<div bind:this={dropdownRef}>
  <button type="button" on:click={() => open = !open}>
    {selectedOption ? selectedOption.label : placeholder}
    <span>▼</span>
  </button>
  {#if open}
    <div>
      {#each options as option}
        <button type="button" on:click={() => selectOption(option)}>
          {option.label}
        </button>
      {/each}
    </div>
  {/if}
</div>
