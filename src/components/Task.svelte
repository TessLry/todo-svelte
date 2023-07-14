<script>
  export let task;
  export let allTasks;

  let canUpdate = false;
  let taskInput;

  function deleteTask() {
    allTasks = allTasks.filter((t) => t !== task);
  }

  function completeTask() {
    task.done = !task.done;
  }

  function handleKeyUp(event) {
    if (event.key === "Enter") {
      canUpdate = !canUpdate;
    }
  }

  $: if (taskInput) taskInput.focus();
</script>

<div class={`task ${task.done ? "completed" : ""}`}>
  {#if task.done}
    <button on:click={completeTask}>
      <i class="fa-regular fa-check-square" />
    </button>
  {:else}
    <button on:click={completeTask}>
      <i class="fa-regular fa-square" />
    </button>
  {/if}

  {#if canUpdate && !task.done}
    <input
      type="text"
      bind:value={task.name}
      on:blur={() => (canUpdate = !canUpdate)}
      bind:this={taskInput}
      on:keyup={handleKeyUp}
    />
  {:else}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
    <p
      on:click={() => (canUpdate = !canUpdate)}
      class={task.done ? "completed" : ""}
    >
      {task.name}
    </p>
  {/if}

  <button on:click={deleteTask}>
    <i class="fa-solid fa-trash" />
  </button>
</div>

<style>
  .task {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-radius: 0.5rem;
    padding: 0.5rem;
  }

  .task p {
    flex: 1;
    font-size: 1rem;
    padding: 0 0.5rem;
    user-select: none;
    word-wrap: break-word;
    cursor: pointer;
  }
  .task p.completed {
    cursor: default;
  }
  input {
    flex: 1;
    max-width: 90%;
    border: none;
    font-size: 1rem;
    padding: 0 0.5rem;
    border-radius: 5px;
  }
  input:focus {
    outline: none;
  }

  button {
    border: none;
    background-color: transparent;
  }

  i {
    color: white;
    font-size: 1.5rem;
    cursor: pointer;
  }
  i:hover {
    transform: scale(1.1);
  }

  .completed {
    text-decoration: line-through;
  }
</style>
