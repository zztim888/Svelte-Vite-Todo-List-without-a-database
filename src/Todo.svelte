<script>
    let newItem = '';
	
    let todoList = [{text: 'Rome', status: true},
                    {text: 'Shenzhen', status: true},                    
                    {text: 'Tokyo', status: true},
                    {text: 'Paris', status: false},
                    {text: 'London', status: false},
                    {text: 'Stockholm', status: false},
                    {text: 'Copenhagen', status: false},
                    {text: 'Oslo', status: false},
                    {text: 'Cape town', status: false},
                    {text: 'Cairo', status: false}];               
                    
	function addToList() {
		todoList = [...todoList, {text: newItem, status: false}];
		newItem = '';
	}
	
	function removeFromList(index) {
		todoList.splice(index, 1)
		todoList = todoList;
    }   
    
</script>

<input bind:value={newItem} type="text" placeholder="Add a City to visit...">
<button on:click={addToList}>Add</button>


<br/>
{#each todoList as item, index}
	<input bind:checked={item.status} type="checkbox">
	<span class:checked={item.status}>{item.text}</span>
	<span on:click={() => removeFromList(index)}>❌</span>
	<br/>
{/each}     

<style> 
	.checked {
        text-decoration: line-through;
        color:grey;
    }  
</style> 