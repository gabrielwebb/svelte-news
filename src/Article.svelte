<script>
  import { onMount } from "svelte";
  //// variables
  const API_KEY = "f1208f5af13143ccb46e6f92a4fae85e";
  const URL = `https://newsapi.org/v2/top-headlines?country=us&category=technology&apiKey=${API_KEY}`;
  let articles = [];

  ///async
  onMount(async function() {
    const response = await fetch(URL);
    const json = await response.json();
    articles = json["articles"];
  });
</script>

<style>
  .card {
    font-family: "Gilda Display", serif;
    margin: 5px;
    border: 4px solid #02070a;
    border-radius: 5px;
    box-shadow: 10px 10px 5px rgb(139, 139, 139);
  }
  .card-body {
    margin-bottom: 30px;
  }

  h3,
  p,
  a {
    margin: 1.5rem;
  }
  a {
    color: inherit;
    text-decoration: none;
  }

  img {
    max-width: 100%;
  }
</style>

{#each articles as article}
  <div class="card">
    {#if article.urlToImage === null}
      <br />
    {:else}
      <img src={article.urlToImage} alt="Article Image" />
    {/if}
    <div class="card-body">
      <h3>{article.title}</h3>
      {#if article.description === null}
        <p />
      {:else}
        <p>{article.description}</p>
      {/if}
      <a href={article.url}>Read story</a>
    </div>
  </div>
{/each}
