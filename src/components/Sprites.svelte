<script>
  export let pokemon;

  $: hasGenderDifference =
    pokemon.sprites.front_female || pokemon.sprites.back_female || pokemon.sprites.front_shiny_female || pokemon.sprites.back_shiny_female;
</script>

<style>
  table {
    background-color: #eee;
    border: 1px solid #ddd;
    border-collapse: separate;
    border-left: 0;
    border-radius: 4px;
    border-spacing: 0px;
    table-layout: fixed;
    width: 100%;

    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
    margin-bottom: 1.5rem;
  }

  thead {
    display: table-header-group;
    vertical-align: middle;
    border-color: inherit;
    border-collapse: separate;
  }

  tr {
    display: table-row;
    vertical-align: inherit;
    border-color: inherit;
  }

  th, td {
    padding: 5px 4px 6px 4px;
    text-align: left;
    vertical-align: top;
    border-left: 1px solid #ddd;
  }

  td {
    border-top: 1px solid #ddd;
    text-align: center;
    vertical-align: center;
  }

  th {
    text-align: center;
    vertical-align: center;
  }

  thead:first-child tr:first-child th:first-child, tbody:first-child tr:first-child td:first-child {
    border-radius: 4px 0 0 0;
  }

  thead:last-child tr:last-child th:first-child, tbody:last-child tr:last-child td:first-child {
    border-radius: 0 0 0 4px;
  }
</style>

{#if !hasGenderDifference}
  <table>
    <thead>
      <tr>
        <th>Front Sprite</th>
        <th>Back Sprite</th>
        <th>Shiny Front Sprite</th>
        <th>Shiny Back Sprite</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><img src={pokemon.sprites.front_default} alt={`${pokemon.name}'s default front sprite`}></td>
        <td><img src={pokemon.sprites.back_default} alt={`${pokemon.name}'s default back sprite`}></td>
        <td><img src={pokemon.sprites.front_shiny} alt={`${pokemon.name}'s shiny front sprite`}></td>
        <td><img src={pokemon.sprites.back_shiny} alt={`${pokemon.name}'s shiny back sprite`}></td>
      </tr>
    </tbody>
  </table>
{:else}
  <table>
    <thead>
      <tr>
        <th>Front Sprite - Female</th>
        <th>Back Sprite - Female</th>
        <th>Shiny Front Sprite - Female</th>
        <th>Shiny Back Sprite - Female</th>
        <th>Front Sprite - Male</th>
        <th>Back Sprite - Male</th>
        <th>Shiny Front Sprite - Male</th>
        <th>Shiny Back Sprite - Male</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <img src={pokemon.sprites.front_female} alt={`${pokemon.name}'s female default front sprite`}>
        </td>
        <td>
          <img src={pokemon.sprites.back_female} alt={`${pokemon.name}'s female default back sprite`}>
        </td>
        <td>
          <img src={pokemon.sprites.front_shiny_female} alt={`${pokemon.name}'s female shiny front sprite`}>
        </td>
        <td>
          <img src={pokemon.sprites.back_shiny_female} alt={`${pokemon.name}'s female shiny back sprite`}>
        </td>
        <td>
          <img src={pokemon.sprites.front_default} alt={`${pokemon.name}'s male default front sprite`}>
        </td>
        <td>
          <img src={pokemon.sprites.back_default} alt={`${pokemon.name}'s male default back sprite`}>
        </td>
        <td>
          <img src={pokemon.sprites.front_shiny} alt={`${pokemon.name}'s male shiny front sprite`}>
        </td>
        <td>
          <img src={pokemon.sprites.back_shiny} alt={`${pokemon.name}'s male shiny back sprite`}>
        </td>
      </tr>
    </tbody>

  </table>
{/if}

