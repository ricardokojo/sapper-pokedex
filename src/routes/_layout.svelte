<script>
  import TheHeader from '../components/TheHeader.svelte';
  import TheFooter from '../components/TheFooter.svelte';
</script>

<style>
  main {
    position: relative;
    max-width: 56em;
    height: 100%;
    padding: 2em;
    margin: 4rem auto;
    box-sizing: border-box;
  }
</style>

<TheHeader />

<main>
  <slot></slot>
</main>

<TheFooter />
