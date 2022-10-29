<script>
  import { each } from "svelte/internal";
  import Characters from "./lib/Characters.svelte";
  import Character from "./lib/Characters.svelte";

  let characters = [];
  let page = 1;

  async function loadCharacter() {
    const res = await fetch(
      "https://rickandmortyapi.com/api/character?page=" + page
    );
    const data = await res.json();
    console.log(data);
    characters = data.results;
  }
  loadCharacter();

  function nextPage() {
    page++;
    loadCharacter();
  }
  function PreviousPage() {
    page--;
    loadCharacter();
  }
</script>

<h1 class="title">Rick and Morty Info</h1>


<div class="container">
  <div class="buttons">
    <button on:click={PreviousPage} disabled={page === 1} class="btn">Previous</button>
    <button on:click={nextPage} class="btn">Next</button>
  </div>
  <div class="grid">

    {#each characters as character}
      <Character {character} />
    {/each}
  </div>
</div>

<style>
  .btn:disabled{
    visibility: hidden;
  }

  .btn{
    margin: 10px;
    width: 80px;
    height: 25px;
    background-color: #ffffff;
    color:var(--main-text-color);
    border: 1px solid #ffca84;
    border-radius: 10px;
    cursor: pointer;
    
  }
  .btn:hover{
    background-color: cornsilk;
    color: #505050;
  }
</style>
