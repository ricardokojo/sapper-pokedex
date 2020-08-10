<script>
  import StatBar from "./StatBar.svelte";

  export let pokemon;

  $: totalStats = pokemon.stats.reduce((acc, stat) => {
    console.log(acc)
    console.log(stat)
    return acc + stat.base_stat;
  }, 0);
</script>

<style>
  .stats {
    display: flex;
    flex-direction: column;

    background-color: #eee;
    border: 1px solid #ddd;
    border-radius: 5px;
    padding: 1rem;

    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
    margin-bottom: 1.5rem;
  }

  h4 {
    font-size: 1.2rem;
    margin: 0 1rem 0 0;

    width: 25%;
  }

  span {
    font-family: "Roboto Mono", monospace;
    font-weight: bold;
    float: right;
  }

  .stat-wrapper {
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
  }

  .stat-wrapper:last-child {
    margin-bottom: 0;
  }
</style>

<div class="stats">
  <div class="stat-wrapper">
    <h4>HP: <span>{pokemon.stats[0].base_stat}</span></h4>
    <StatBar statValue={pokemon.stats[0].base_stat} />
  </div>
  <div class="stat-wrapper">
    <h4>Attack: <span>{pokemon.stats[1].base_stat}</span></h4>
    <StatBar statValue={pokemon.stats[1].base_stat} />
  </div>
  <div class="stat-wrapper">
    <h4>Defense: <span>{pokemon.stats[2].base_stat}</span></h4>
    <StatBar statValue={pokemon.stats[2].base_stat} />
  </div>
  <div class="stat-wrapper">
    <h4>Special Attack: <span>{pokemon.stats[3].base_stat}</span></h4>
    <StatBar statValue={pokemon.stats[3].base_stat} />
  </div>
  <div class="stat-wrapper">
    <h4>Special Defense: <span>{pokemon.stats[4].base_stat}</span></h4>
    <StatBar statValue={pokemon.stats[4].base_stat} />
  </div>
  <div class="stat-wrapper">
    <h4>Speed: <span>{pokemon.stats[5].base_stat}</span></h4>
    <StatBar statValue={pokemon.stats[5].base_stat} />
  </div>
  <div class="stat-wrapper">
    <h4>Total: <span>{totalStats}</span></h4>
  </div>
</div>
