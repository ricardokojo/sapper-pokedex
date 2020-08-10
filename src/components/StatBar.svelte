<script>
  export let statValue;

  $: statBasedWidth = (statValue / 255) * 100;
  $: statBasedClass = statValue >= 100 ? 'high' : statValue >= 60 ? 'average' : 'low';
</script>

<style>
.stat {
  background-color: #fefefe;
  border-radius: 5px;
  height: 2rem;
  width: 100%;

  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
}

.stat-bar {
  border-radius: 5px;
  height: inherit;
}

.low {
  background-color: #f93131;
  border: 1px solid #ee2b2b;
}

.average {
  background-color: #ffdd57;
  border: 1px solid #ebcb4b;
}

.high {
  background-color: #06ae06;
  border: 1px solid #069d06;
}
</style>

<div class="stat">
  <div class={`stat-bar ${statBasedClass}`} role="progressbar" style={`width: ${statBasedWidth}%`}>
  </div>
</div>
