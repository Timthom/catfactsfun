<script>
  import { onMount } from "svelte";


  let count = 1
  const increment = () => {
    count += 1
  }

  let promise;
  onMount(async () => {
    promise = getRandomCatFacts();
  });

  const getRandomCatFacts = async () => {
    const res = await fetch("https://catfact.ninja/fact");
    const json = await res.json();

    if (json.fact) {
      return json.fact;
    } else {
      throw new Error("Not found any interesting facts");
    }
  };

  const reload = () => {
    promise = getRandomCatFacts();
  };
</script>

<div class="cat-fact-container">
  {#await promise}
    <p>...loading...</p>
  {:then fact}
    <p><em>{fact}</em></p>
    <p class="counting"> You have read {count} facts today! </p>
  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}
</div>
<button on:click={() => reload() } on:click={increment}>One more fact?</button>


<style>
  .cat-fact-container {
    border: 0.2rem solid #ccc;
    padding: 5rem;
    margin: 2rem;
    border-radius: 1rem;
    background-color: beige;
  }
  p {
    margin: 1rem auto;
    line-height: 1.35;
  }
  .counting {
    padding-top: 1rem;
  }

  button {
    padding: 1rem 2rem;
    background-color: olive;
    color: white;
    font-weight: bold;
    text-transform: uppercase;
    border: 0px;
    border-radius: 1rem;
    box-shadow: 2px 2px 5px grey;
  }

  @media (max-width: 480px) {

    .cat-fact-container {
    padding: 2rem;
    margin: 1rem;
    }
  }


</style>
