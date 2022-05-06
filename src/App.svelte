<script>
  import logo from "./assets/cat.png";
  import logo2 from "./assets/black-cat.png";

  import CatFacts from "./lib/CatFacts.svelte";
  
</script>

<main>
  <img src={logo} alt="Cool Cat Logo" />
  <img src={logo2} alt="Cool cat" />
  <h1>CatFacts!</h1>

  <CatFacts />

  
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 12rem;
    width: 12rem;
  }

  h1 {
    color: olive;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 400;
    line-height: 1.1;
    margin: 2rem auto;
  }

  
</style>
