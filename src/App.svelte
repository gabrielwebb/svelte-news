<script>
  import { onMount } from "svelte";
  import Header from "./Header.svelte";
  import Article from "./Article.svelte";
</script>

<style>
  div {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(305px, 1fr));
    grid-gap: 15px;
    margin-top: 1.5rem;
  }
</style>

<Header />
<div>
  <Article />
</div>
