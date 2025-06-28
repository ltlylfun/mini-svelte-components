<script>
  export let options = [];
  export let value = [];
  export let onChange = (newValue) => {};
  
  function handleChange(optionValue) {
    if (value.includes(optionValue)) {
      onChange(value.filter(v => v !== optionValue));
    } else {
      onChange([...value, optionValue]);
    }
  }
</script>

<div>
  {#each options as option}
    <label>
      <input
        type="checkbox"
        checked={value.includes(option.value)}
        on:change={() => handleChange(option.value)}
      />
      {option.label}
    </label>
  {/each}
</div>
