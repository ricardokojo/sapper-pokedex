<script>
</script>

<style>
</style>

<svelte:head>
  <title>Hackday 10/08 - Sapper Pokédex</title>
</svelte:head>

<ol>
  {#each Array(151) as _, i}
    <li>
      <a href={`pokemon/${i + 1}`}>{i + 1}</a>
    </li>
  {/each}
</ol>
