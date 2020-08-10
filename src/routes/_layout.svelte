<script>
  import TheHeader from '../components/TheHeader.svelte';
  import TheFooter from '../components/TheFooter.svelte';
</script>

<style>
main {
  margin-top: 6rem;
  margin-bottom: 4rem;
  margin-left: auto;
  margin-right: auto;
  width: 100%;
}

@media (min-width: 640px) {
  main {
    max-width: 640px;
  }
}

@media (min-width: 768px) {
  main {
    max-width: 768px;
  }
}

@media (min-width: 1024px) {
  main {
    max-width: 1024px;
  }
}

@media (min-width: 1280px) {
  main {
    max-width: 1280px;
  }
}
</style>

<TheHeader />

<main>
  <slot></slot>
</main>

<TheFooter />
