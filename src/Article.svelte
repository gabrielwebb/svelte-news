<script>
  import { onMount } from "svelte";
  //// variables
  const API_KEY = "f1208f5af13143ccb46e6f92a4fae85e";
  const URL = `https://newsapi.org/v2/top-headlines?country=us&category=entertainment&apiKey=${API_KEY}`;
  let articles = [];

  ///async
  onMount(async function() {
    const response = await fetch(URL);
    const json = await response.json();
    articles = json["articles"];
  });
</script>

<style>
  .container > .card img {
    max-width: 100%;
  }
  .card {
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
  p {
    overflow-wrap: break-word;
  }

  a {
    color: inherit;
    text-decoration: none;
  }
</style>

{#each articles as article}
  <div class="card">
    <img src={article.urlToImage} alt="Article Image" />
    <div class="card-body">
      <h3>{article.title}</h3>
      <p>{article.description}</p>
      <a href={article.url}>Read story</a>
    </div>
  </div>
{/each}
