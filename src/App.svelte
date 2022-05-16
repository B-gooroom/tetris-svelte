<script>
  import Header from "./components/Header.svelte";
  import Tetris from "./components/Tetris.svelte";
</script>

<main>
  <Header />
  <Tetris />
</main>

<style global lang="scss">

  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
