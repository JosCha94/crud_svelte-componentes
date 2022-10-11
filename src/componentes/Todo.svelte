<script>
// @ts-nocheck

  import { todos, opc } from "../stores";

  export let item;

  const delTodos = (id) => {
    todos.delete(id);
    opc.mostrar({
      texto: "Se ha borrado",
      color: "bg-danger",
      estado: true,
    });
    // mostrarToast(, );
  };

  const updateTodos = (id) => {
    todos.put(id);
    opc.mostrar({
      texto: "Se ha actualizado",
      color: "bg-warning",
      estado: true,
    });
    // mostrarToast(, );
  };

  const classEstado = (valor) =>
    valor ? "btn btn-sm btn-success" : "btn btn-sm btn-warning";

  const classIcono = (valor) =>
    valor ? "bi bi-arrow-clockwise" : "bi bi-check2";
</script>

<div class="shadow my-3 p-3 lead">
  <p class={item.estado ? "text-decoration-line-through" : ""}>
    {item.texto}
  </p>
  
  <button class="btn {classEstado(item.estado)}" on:click={updateTodos(item.id)}>
    <i class={classIcono(item.estado)} />
  </button>

  <button class="btn btn-sm btn-danger" on:click={delTodos(item.id)}>
    <i class="bi bi-trash" />
  </button>
</div>
