<script>
  export let allTasks = [];

  let value = "";

  function addTask() {
    if (!value) return;
    allTasks = [...allTasks, { name: value, done: false }];
    value = "";
  }

  function handleKeyUp(event) {
    if (event.key === "Enter") {
      addTask();
    }
  }
</script>

<div class="add-zone">
  <span>
    <input placeholder="Add a task..." bind:value on:keyup={handleKeyUp} />
    {#if value}
      <button on:click={addTask}>
        <i class="fa-solid fa-square-plus" />
      </button>
    {/if}
  </span>
</div>

<style>
  .add-zone {
    margin: 2rem;
  }

  span {
    display: flex;
    border: 2px solid var(--pink);
    border-radius: 0.5rem;
  }

  input {
    flex: 1;
    border: none;
    font-size: 1.5rem;
    padding: 0.5rem;
    padding-right: 1rem;
    background: transparent;
  }
  input:focus {
    outline: none;
  }

  button {
    border: none;
    background-color: transparent;
  }

  i {
    color: var(--dark-pink);
    font-size: 2.5rem;
    cursor: pointer;
  }
</style>
