<script>

import {opc, todos} from "../stores"

  let todo = { id: "", texto: "", estado: false };

  const addTodo = () => {
    if (!todo.texto.trim()) {
      console.log("vacio");
      todo.texto = "";
      return;
    }

    // @ts-ignore
    todo.id = Date.now();
    todos.add(todo)
    console.log(todos);
    todo = { id: "", texto: "", estado: false };

    opc.mostrar({
        texto: "Se agrego correctamente",
        color: "bg-primary",
        estado: true
    })

    // mostrarToast(, );
  };
</script>

<form on:submit|preventDefault={addTodo}>
  <input
    type="text"
    placeholder="Enter para agregar"
    class="form-control shadow border-0"
    bind:value={todo.texto}
  />
</form>
