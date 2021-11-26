<script>
  import Card from "./Card.svelte";

  export let suit = "1";
  export let num = "1";
</script>

<div class="cardSelect">
  <Card bind:suit bind:num />
  <select name="num" bind:value={num}>
    <option value="1">A</option>
    <option value="2">2</option>
    <option value="3">3</option>
    <option value="4">4</option>
    <option value="5">5</option>
    <option value="6">6</option>
    <option value="7">7</option>
    <option value="8">8</option>
    <option value="9">9</option>
    <option value="10">10</option>
    <option value="11">J</option>
    <option value="12">Q</option>
    <option value="13">K</option>
  </select>
  <select name="suit" bind:value={suit}>
    <option value="1">♣</option>
    <option value="2">♥</option>
    <option value="3">♠</option>
    <option value="4">♦</option>
  </select>
</div>

<style>
  .cardSelect {
    margin: 1rem;
    display: block;
  }
</style>
