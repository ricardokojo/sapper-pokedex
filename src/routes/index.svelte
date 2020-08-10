<script>
</script>

<style>
.pokemon-list {
  display: flex;
  flex-flow: wrap;
  align-items: center;
  justify-content: center;
}

.pokemon-link {
  box-shadow: none;
  border-radius: 5px;
  text-decoration: none;
  transition: box-shadow 0.1s;
}

.pokemon-link:hover {
  box-shadow: 0 0 1rem .1rem #333;
}
</style>

<svelte:head>
  <title>Hackday 10/08 - Sapper Pokédex</title>
</svelte:head>

<div class="pokemon-list">
  {#each Array(151) as _, i}
    <a href={`pokemon/${i + 1}`} class="pokemon-link">
      <img src={`box-sprites/${(i + 1).toString().padStart(3, "0")}.png`} alt={`Box sprite for Pokémon number ${i + 1}`}>
    </a>
  {/each}
</div>

