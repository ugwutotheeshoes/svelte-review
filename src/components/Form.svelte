<script>
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  import Ratings from "./Ratings.svelte";
  let text = "";
  let rating = 10
  let btnDisabled = true;
  let message;

  const handleInput = () => {
    let min = 10;
    if (text.trim().length <= min) {
      message = `Text must be at least ${min} characters`;
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate your service with us?</h2>
  </header>
  <form action="">
      <Ratings />
    <div class="inputs">
      <input
        type="text"
        on:input={handleInput}
        bind:value={text}
        placeholder="Write a review."
      />
      <Button disabled={btnDisabled} type="submit">send</Button>
    </div>
    {#if message}
      <div class="message">
        {message}
      </div>
    {/if}
  </form>
</Card>

<style>
  header,
  .message {
    text-align: center;
    text-transform: uppercase;
  }
  .inputs {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  input {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    border: 1px solid rgb(206, 203, 203);
    color: #39355C;
    font-size: 1rem;
    border-radius: 8px;
    width: 300px;
    height: 36px;
    padding-left: 10px;
    margin-right: 5px;
  }
</style>
