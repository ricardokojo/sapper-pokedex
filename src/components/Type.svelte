<script>
  export let type = "normal";
</script>

<style>
  span {
    display: flex;
    align-items: center;
    justify-content: center;

    border-radius: 5px;
    color: #fefefe;
    font-family: "Roboto Mono", monospace;
    letter-spacing: 0.1em;
    font-size: 1rem;
    font-weight: bold;
    text-transform: uppercase;

    margin-right: 0.25rem;
    padding: .5rem 1rem;
  }

  span > img {
    margin-right: 0.25rem;
    width: 1.25rem;
  }

  .bug {
    background-color: #91c12f;
  }

  .dark {
    background-color: #5a5465;
  }

  .dragon {
    background-color: #0b6dc3;
  }

  .electric {
    background-color: #f4d23c;
  }

  .fairy {
    background-color: #ec8fe6;
  }

  .fighting {
    background-color: #ce416b;
  }

  .fire {
    background-color: #ff9d55;
  }

  .flying {
    background-color: #8fa9de;
  }

  .ghost {
    background-color: #5269ad;
  }

  .grass {
    background-color: #63bc5a;
  }

  .ground {
    background-color: #d97845;
  }

  .ice {
    background-color: #73cec0;
  }

  .normal {
    background-color: #919aa2;
  }

  .poison {
    background-color: #aa6bc8;
  }

  .psychic {
    background-color: #fa7179;
  }

  .rock {
    background-color: #c5b78c;
  }

  .steel {
    background-color: #5a8ea2;
  }

  .water {
    background-color: #5090d6;
  }
</style>

<span class={`type ${type}`}><img src={`types/${type}.png`} alt={`${type} type's icon`}> {type}</span>
