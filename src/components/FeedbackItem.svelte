<script>
  import { createEventDispatcher } from "svelte";
  import Card from "./Card.svelte";

  export let item = "";
  const dispatch = createEventDispatcher();
  const handleDelete = (itemId) => {
    dispatch("delete-feedback", itemId);
  };
</script>

<Card>
  <div class="number">
    {item.rating}
  </div>
  <div class="close" on:click={() => handleDelete(item.id)}>x</div>
  <p class="text">{item.text}</p>
</Card>

<style>
  .number {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    position: absolute;
    top: -10px;
    left: -10px;
    width: 30px;
    height: 30px;
    background: #9ed8c0;
    color: #39355C;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }

  .close {
    position: absolute;
    top: 2px;
    right: 20px;
    color: #f51e1e;
    cursor: pointer;
    font-weight: 700;
    font-size: 1.5rem;
  }
</style>
