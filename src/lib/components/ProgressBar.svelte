<script>
  export let value = 0;
  export let max = 100;
  
  $: percentage = (value / max) * 100;
</script>

<div>
  <div style="width: 200px; height: 10px; background: #eee">
    <div
      style="width: {percentage}%; height: 100%; background: #409eff"
    ></div>
  </div>
  <span>
    {value} / {max}
  </span>
</div>
