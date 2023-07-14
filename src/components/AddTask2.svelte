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
  <input placeholder="Add a task..." bind:value on:keyup={handleKeyUp} />
  <button on:click={addTask}> Add </button>
</div>

<style>
  .add-zone {
    margin: 2rem;
    display: flex;
  }

  input {
    flex: 1;
    border: 2px solid var(--dark-pink);
    border-radius: 0.5rem 0 0 0.5rem;
    font-size: 1.5rem;
    padding: 0.5rem;
  }
  input:focus {
    outline: none;
  }

  button {
    border: none;
    border-radius: 0 0.5rem 0.5rem 0;
    background-color: var(--dark-pink);
    color: white;
    font-size: 1.5rem;
    cursor: pointer;
    padding: 0.5rem;
  }
</style>
