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
  import Stats from '../../components/Stats.svelte';
  import Sprites from '../../components/Sprites.svelte'

  export let pokemon;
  const lastPokemonNumber = 807; // PokeAPI contains information up to Zeraora (807)
  console.log(pokemon);

  $: paddedNumber = pokemon.id.toString().padStart(3, "0");
  $: previousPokemonNumber = pokemon.id - 1;
  $: nextPokemonNumber = pokemon.id + 1;
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

  .bottom-links {
    display: flex;
  }

  .bottom-links .previous {
    margin-right: auto;
  }

  .bottom-links .next {
    margin-left: auto;
  }
</style>

<svelte:head>
  <title>{paddedNumber} — {pokemon.name.toUpperCase()} | Sapper Pokédex</title>
</svelte:head>

<a href="/">‹ Voltar ao início</a>

<h1>{paddedNumber} — <span>{pokemon.name}</span></h1>

<BasicInfo pokemon={pokemon}/>

<Stats pokemon={pokemon}/>

<Sprites pokemon={pokemon}/>

<div class="bottom-links">
  {#if previousPokemonNumber > 0}
    <a href={`/pokemon/${previousPokemonNumber}`} class="previous">‹ Anterior</a>
  {/if}
  {#if nextPokemonNumber <= lastPokemonNumber}
    <a href={`/pokemon/${nextPokemonNumber}`} class="next">Próximo ›</a>
  {/if}
</div>
