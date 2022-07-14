<script>
  import { v4 as uuidv4 } from "uuid";
  import Card from "./Card.svelte";
  import { createEventDispatcher } from "svelte";
  import Button from "./Button.svelte";
  import Ratings from "./Ratings.svelte";

  const dispatch = createEventDispatcher();

  let text = "";
  let rating = 10;
  let min = 10;
  let btnDisabled = true;
  let message;

  const handleSelect = (e) => (rating = e.detail);

  const handleInput = () => {
    if (text.trim().length <= min) {
      message = `Text must be at least ${min} characters`;
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };

  const handleSubmit = () => {
    if (text.trim().length > min) {
      const newFeedback = {
        id: uuidv4(),
        text,
        rating: +rating,
      };
      dispatch("add-feedback", newFeedback);
      text = ''
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate your service with us?</h2>
  </header>
  <form on:submit|preventDefault={handleSubmit}>
    <Ratings on:rating-select={handleSelect} />
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
    color: #39355c;
    font-size: 1rem;
    border-radius: 8px;
    width: 300px;
    height: 36px;
    padding-left: 10px;
    margin-right: 5px;
  }
</style>
