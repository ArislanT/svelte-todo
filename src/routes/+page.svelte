<!-- The form, list, and the state-->
<script>
    // within script or else treated as plain text, import the component for the todo item
    import TodoItem from '$lib/components/TodoItem.svelte';
    // varaible needed for the todo list, states so it can be reactive
    let todos = $state([]); // the list of todos
    let newText = $state(''); // the new string todo text
    let newDue = $state(''); // the new string todo due date

    // + function to add a new todo to the list, takes event
    function addTodo(event) {
        event.preventDefault();
        if (!newText.trim()) return; //if no text, return
        // id for unique indetifier, text for todo text, due for newDue, done boolean for checkbox
        todos.push({ id: Date.now(), text: newText, due: newDue, done: false});
        newText = ''; // reset newText to empty string
        newDue = ''; // reset newDue to empty string
    }
    // removes todo from list when delete button is clicked, takes id of todo to delete
    function deleteTodo(id){
        todos = todos.filter((t) => t.id !== id)
    }
</script>

<!-- checkbox button-->
 <h1>Todos</h1>
<!--Creation of new todo-->
 <form onsubmit={addTodo}>
    <!-- bind for connectivity between the input and the variables-->
    <input bind:value={newText} placeholder="Todo text" />
    <input type="date" bind:value={newDue} placeholder="MM/DD/YYYY" />
    <button type="submit">Add Todo</button>
 </form>

<!-- -->
 <ul>
	{#each todos as todo, i (todo.id)}
        <!-- make prop callback for deleteTodo, going to give to component-->
		<TodoItem bind:todo={todos[i]} ondelete={deleteTodo} />
	{/each}
</ul>