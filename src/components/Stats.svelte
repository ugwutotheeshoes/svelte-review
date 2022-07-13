<script>
  export let count;
  export let average;
</script>

<div class="stats">
  <h4>{count} Reviews</h4>
  {#if average > 0}
  <h4>Ratings average: {average.toFixed(2)}</h4>
  {:else}
  <h4>Ratings average: 0</h4>
  {/if}
</div>

<style>
  .stats {
    display: flex;
    justify-content: space-between;
    text-transform: uppercase;
    align-items: center;
    color: #39355C;
    letter-spacing: 1px;
    font-size: 1rem;
  }
</style>
