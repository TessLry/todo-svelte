<script>
  import Task from "./Task.svelte";

  export let allTasks;
</script>

<div class="all-tasks">
  <div class="uncompleted-task">
    <h2>Uncompleted Tasks</h2>
    <hr />
    {#each allTasks as task}
      {#if !task.done}
        <Task bind:task bind:allTasks />
      {/if}
    {/each}
    {#if !allTasks.some((t) => !t.done)}
      <p>No tasks to do!</p>
    {/if}
  </div>

  <div class="completed-task">
    <h2>Completed Tasks</h2>
    <hr />
    {#each allTasks as task}
      {#if task.done}
        <Task bind:task bind:allTasks />
      {/if}
    {/each}
    {#if !allTasks.some((t) => t.done)}
      <p>No tasks completed!</p>
    {/if}
  </div>
</div>

<style>
  .all-tasks {
    width: 30%;
  }

  h2 {
    color: white;
    font-size: 2rem;
  }

  hr {
    border: 1px dashed white;
    margin: 0.5rem 0;
  }

  .uncompleted-task,
  .completed-task {
    border-radius: 0.5rem;
    padding: 1rem;
    margin: 1rem 0;
  }

  .uncompleted-task {
    background-color: var(--pink);
    border: 1px solid var(--pink);
  }
  .completed-task {
    background-color: var(--light-blue);
    border: 1px solid var(--light-blue);
  }
</style>
