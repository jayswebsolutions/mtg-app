<script>
    export let team
    export let score
    export let gameOver

    function add() {
        score += 1
    }

    function minus() {
        score -= 1
    }
    
</script>

<h2>Team {team}: {score}</h2>
<div class="score">
    <button disabled={gameOver} on:click={add}  class="plus">+</button>
    <button disabled={gameOver} on:click={minus} class="minus">-</button>
</div>

<style>

    .plus {
        background-color: green;
        color: white;
    }

    .minus {
        background-color: red;
        color: white;
    }
</style>