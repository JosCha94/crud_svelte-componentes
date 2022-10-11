<script>
  // @ts-nocheck
  import { todos } from "./stores";
  import AddTodo from "./componentes/AddTodo.svelte";
  import Todo from "./componentes/Todo.svelte";
  import Toast from "./componentes/Toast.svelte";

  if (localStorage.getItem("todos")) {
    todos.local(JSON.parse(localStorage.getItem("todos")));
  }

  $: localStorage.setItem("todos", JSON.stringify($todos));
</script>

<div class="container">
  <h1 class="my-4">CRUD</h1>
  <AddTodo />

  {#each $todos as item}
    <Todo {item} />
  {/each}

  <Toast />
</div>
