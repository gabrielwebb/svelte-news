<script>
  import { onMount } from "svelte";
  import Header from "./Header.svelte";
  import Article from "./Article.svelte";
</script>

<style>
  * {
    font-family: "Gilda Display", serif;
  }
  .container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(305px, 1fr));
    grid-gap: 15px;
    margin-top: 1.5rem;
  }
</style>

<div class="header">

  <Header />
</div>

<div class="container">
  <Article />

</div>
