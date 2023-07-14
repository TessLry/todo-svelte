<script>
  import ListTasks from "./components/ListTasks.svelte";
  import AddTask from "./components/AddTask.svelte";

  let allTasks = localStorage.getItem("todos")
    ? JSON.parse(localStorage.getItem("todos"))
    : [];

  $: {
    localStorage.setItem("todos", JSON.stringify(allTasks));
  }
</script>

<div class="title">
  <h1>TO DO List</h1>
  <i class="fa-solid fa-list-check" />
</div>

<section>
  <AddTask bind:allTasks />
  <ListTasks bind:allTasks />
</section>

<style>
  .title {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: var(--dark-pink);
    color: white;
  }
  h1 {
    font-size: 3rem;
    padding: 1rem;
  }
  i {
    font-size: 2rem;
    padding: 1rem;
  }

  section {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
