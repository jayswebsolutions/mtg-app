<script>

  import Team from './Team.svelte'


  let redScore = 20
  let blueScore = 20

  $: redWon = blueScore  === 0

  $: blueWon = redScore === 0

  $: gameOver = redWon || blueWon




  



  function resetGame() {
      location.reload()
  }

</script>


<div class="container">
  <div class="heading"><h1>MTG Counter App</h1></div>
  <div class="red-team">
      <Team {gameOver} team='red' bind:score={redScore} />
  </div>
  <div class="blue-team">
     <Team {gameOver} team='blue' bind:score={blueScore} />
  </div>
  {#if !gameOver}
  <div id="reset" class="reset"><button on:click={resetGame}>Reset Game</button></div>
  {:else}
      {#if blueWon}
          <h2 style="color: blue; font-size: 2rem; text-align: center;">Blue Won</h2>
          {:else}
          <h2 style="color: red; font-size: 2rem; text-align: center;">Red Won</h2>
      {/if}
  <div id="reset" class="reset"><button on:click={resetGame}>New Game</button></div>
  {/if}

</div>

<style>
  .container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-areas: 
          "a a"
          "b c"
          "d d"
      ;
      width: 90%;
      margin: auto;
      text-align: center;
  }

  .heading {
      grid-area: a;
  }

  .red-team {
      grid-area: b;
      width: 250px;
      height: 100px;
      border: 3px dashed red;
      color: red;
  }

  .blue-team {
      grid-area: c;
      width: 250px;
      height: 100px;
      border: 3px dashed blue;
      color: blue;
  }

  .reset {
      grid-area: d;
      margin-top: 2rem;
  }

  button {
      border: none;
      font-size: 1.25em;
      border-radius: 5px;
  }

  .reset button {
      width: 100%;
      background-color: orange; 
      padding: .25rem;
  }








</style>
