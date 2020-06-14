<script>
import { createEventDispatcher} from "svelte";

const dispatch = createEventDispatcher();
export let lengthh 
let todocontent=''
let todo = {
		id : "",
		content : "",
		completed: ""
	};

function addtodo(e){
    e.preventDefault();
    todo['id'] =  lengthh+1
    todo['content'] = todocontent
    todo['completed'] = false
    dispatch("addtodo", todo);
    console.log(todo)
    todo = {
		id : "",
		content : "",
		completed: ""
	};
	}



</script>

<form on:submit|preventDefault = '{addtodo}'>
 
    <label for="name">add todo </label>
    <input type="text"  id="todo" bind:value ={todocontent} required>
		<div>{todocontent} added</div>
 
 
    <input type="submit" value="Subscribe!">
  
</form>