<script>
  export {};
  let name = "what up";
  let input = "";

  let todos = [{ name: "item1", done: false }, { name: "item2", done: false }];

  $: filtered = todos.filter(item => item.done);
</script>

<style>
	h1 {
	  color: purple;
	}
	span {
	  cursor: pointer;
	}
</style>

<h1>Hello {name}!</h1>

<input bind:value={input} value="" /> You sayin {input}
<br/>
<button on:click={()=>{todos.push({name:input}); todos = todos;}}>Add</button>
{#each todos as todo}
<li on:click={()=>todo.done=!todo.done}><span>{todo.name}</span></li>
{/each}

<h2>Remaining</h2>
{#each filtered as todo}
<li>{todo.name}</li>
{/each}