<script>
  import Board from "./Board.svelte";
  import Header from "./Header.svelte";
  import Search from "./Search.svelte";
</script>

<Header />

<main>
  <Search />

  <Board />
</main>

<style lang="scss">
  main {
    width: 100%;
    height: 100%;
  }
</style>
