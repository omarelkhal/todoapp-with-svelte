<script>
import Todoform from './component/Todoform.svelte';
let name = 'world';
 var todos =[
		{
			id : 1,
			content : 'task1',
			completed: false
		},
		
			{
			id : 2,
			content : 'task2',
			completed: false
		},
		
			{
			id : 3,
			content : 'task3',
			completed: false
		}
	];


function completed(e){
	let todoid = e.target.id
	if(e.target.checked){
todos[todoid-1].completed = true;
		}else{
			todos[todoid-1].completed = false;

		}
}

	let todolength = 3;


const addtodo = (e) => {
	let addedtodo = e.detail
	todos = [...todos, addedtodo]
	todolength++
idcorrector()

}
let thistodo =''

const deletetodo = (e) => {
	let pointer = parseInt(e.target.id, 10);
	todos = todos.filter((a) => a.id !== pointer )
		todolength--
idcorrector()
}
const  idcorrector = () => {
	
	// for (var i = 0; i < todos.length; i++) {
	// 	todos[i].id = i+1

	// }
	todos.forEach((a, b) => a.id = b+1)
	
}
	idcorrector()

</script>
{#each todos as todo}
<h2>{todo.id}</h2>
<h1>{todo.content}</h1>
<input id = '{todo.id}' type = "checkbox" on:click = {completed} >
<input id = {todo.id} type="checkbox" on:click = {deletetodo} >
{#if todo.completed === true}

<h1>completed</h1>
{:else}
{/if}

{/each}
<Todoform lengthh = {todolength} on:addtodo = {addtodo} />


