<!-- Component for a single todo item -->
<script> 
    // hand component delete function. Calls deleteTodo
    let { todo = $bindable(), ondelete } = $props(); // props for the todo item and the delete function
</script>

<li>
    <input type="checkbox" bind:checked={todo.done} />
            <span class:done={todo.done}>{todo.text} </span>
            {#if todo.due}<small>due {todo.due}</small>{/if}
            <button onclick={() => ondelete(todo.id)}>Delete</button>
</li>

<!-- 
List of todos 
 <u1>
    // For each todo fill it out as in populate the box, give its variables with it and if checked delete
    {#each todos as todo (todo.id)}
        <li>
            <input type="checkbox" bind:checked={todo.done} />
            <span class:done={todo.done}>{todo.text} </span>
            {#if todo.due}<small>due {todo.due}</small>{/if}
            <button onclick={() => deleteTodo(todo.id)}>Delete</button>
        </li>
    {/each}
 </u1>
-->

 <!-- Visual-->
 <style>
    .done {
        text-decoration: line-through;
        opacity: 0.6;
    }
 </style>



