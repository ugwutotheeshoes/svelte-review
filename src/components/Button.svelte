<script>
  export let style = "primary";
  export let type = "button";
  export let disabled = false;
</script>

<button {type} {disabled} class={style}> <slot>ss</slot></button>

<style>
  button {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    color: #fff;
    border: 0;
    border-radius: 8px;
    width: 100px;
    height: 41px;
    cursor: pointer;
  }

  .primary {
    border: none;
    background: #9ed8c0;
    color: #39355c;
    text-transform: uppercase;
    font-size: 1rem;
    letter-spacing: 2px;
    font-weight: 600;
    border-radius: 8px;
    width: 100px;
    height: 40px;
    cursor: pointer;
  }

  .secondary {
    background: #ff6a95;
  }

  button:hover {
    transform: scale(0.98);
    opacity: 0.9;
  }

  button:disabled {
    background: #ccc;
    color: #333;
    cursor: auto;
  }

  button:disabled {
    transform: scale(1);
    opacity: 1;
  }
</style>
