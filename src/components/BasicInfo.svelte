<script>
  import Type from './Type.svelte';

  export let pokemon;
  $: mainImage =
    pokemon.sprites.other["official-artwork"].front_default ?
      pokemon.sprites.other["official-artwork"].front_default : pokemon.sprites.front_default;
  $: heightInMeters = pokemon.height / 10;
  $: weightInKilograms = pokemon.weight / 10;

  function parseAbilityName(ability) {
    return ability.replace('-', ' ').replace(/\b\w/g, l => l.toUpperCase());
  }
</script>

<style>
  .basic-info {
    display: flex;
  }

  .main-img {
    /* height: fit-content; */
    width: 50%;
  }

  aside {
    display: flex;
    flex-direction: column;
    width: 50%;
  }

  aside .types {
    display: flex;
    margin-bottom: 1.5rem;
  }

  ol {
    padding: 0;
    margin: 0;
    list-style: none;
  }

  ol > li {
    font-size: 1.2rem;
    text-transform: capitalize;
  }

  h2 {
    font-size: 2rem;
    margin-top: 0;
    margin-bottom: 1.5rem;
  }

  h3 {
    font-size: 1.5rem;
    margin-top: 0;
    margin-bottom: 0.5rem;
  }

  p {
    font-size: 1.2rem;
    margin-top: 0;
    margin-bottom: 1.5rem;
  }
</style>

<div class="basic-info">
  <img src={mainImage} class="main-img" alt={`${pokemon.name}'s main picture`}>
  <aside>
    <h2>Basic Information</h2>

    <h3>Type: </h3>
    <div class="types">
      {#each pokemon.types as type}
        <Type type={type.type.name} />
      {/each}
    </div>

    <h3>Height:</h3>
    <p>{heightInMeters} m</p>

    <h3>Weight:</h3>
    <p>{weightInKilograms} kg</p>

    <h3>Abilities:</h3>
    <ol>
      {#each pokemon.abilities as ability}
        <li>{parseAbilityName(ability.ability.name)} {#if ability.is_hidden}(Hidden Ability){/if}</li>
      {/each}
    </ol>
  </aside>
</div>
