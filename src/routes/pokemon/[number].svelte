<script context="module">
  export async function preload({ params, query }) {
    const data = await this.fetch(`https://pokeapi.co/api/v2/pokemon/${params.number}`)
      .then(res => res.json())
      .then(data => data)
      .catch(err => this.error(500, err));
    return {pokemon: data};
  }
</script>

<script>
  export let pokemon;

  $: paddedNumber = pokemon.id.toString().padStart(3, "0");
</script>

<svelte:head>
  <title>{paddedNumber} - {pokemon.name.toUpperCase()} | Sapper Pokédex</title>
</svelte:head>

<a href="/">‹ Voltar ao início</a>

<h1>{paddedNumber} - {pokemon.name}</h1>

<div class="base">
  <img src={pokemon.sprites.other["official-artwork"].front_default} class="img" alt={`${pokemon.name}'s official artwork`}>
  <div class="info">
    <h2>
      {#each pokemon.types as type}
        <span class="type {type.type.name}">{type.type.name}</span>
      {/each}
    </h2>
    <p>{pokemon.height / 10}m</p>
    <p>{pokemon.weight / 10}kg</p>
    <ol>
      {#each pokemon.abilities as ability}
        <li>{ability.ability.name} {ability.is_hidden}</li>
      {/each}
    </ol>
  </div>
</div>

<div class=''>
  <ul>
    {#each pokemon.stats as stat}
      <li>{stat.base_stat}</li>
    {/each}
  </ul>

  {#each Object.entries(pokemon.sprites) as [key, value]}
    {key}
    <img src={value}/>
  {/each}
</div>
