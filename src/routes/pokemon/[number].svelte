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
  import BasicInfo from '../../components/BasicInfo.svelte';

  export let pokemon;
  console.log(pokemon);

  $: paddedNumber = pokemon.id.toString().padStart(3, "0");
</script>

<style>
  a {
    color: #777;
    font-size: 1.25rem;
    text-decoration: none;
  }

  a:hover {
    color: #666;
    text-decoration: underline;
  }

  h1 {
    font-size: 3rem;
    margin: 0.5rem 0;
  }

  h1 > span {
    text-transform: capitalize;
  }
</style>

<svelte:head>
  <title>{paddedNumber} — {pokemon.name.toUpperCase()} | Sapper Pokédex</title>
</svelte:head>

<a href="/">‹ Voltar ao início</a>

<h1>{paddedNumber} — <span>{pokemon.name}</span></h1>

<BasicInfo pokemon={pokemon} />

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
