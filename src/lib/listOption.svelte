<script>
    export let options 
</script>

<nav>
    <select>
        {#each options as option}
        <optgroup label="{option.groupName}">
            {#each option.options as childOption}
                <option value="{childOption.value}">{childOption.label}</option>
            {/each}
        </optgroup>
        {/each}
    </select>
</nav>
    
<style>
    nav{
		text-align: center;
	}
	select{
		width: 500px;
		padding: 6px;
		margin-top: 6px;
		margin-bottom: 6px;
		border-color: rgb(156, 156, 156);
		border-radius: 8px;
	}
	optgroup {
        border-radius: 10px;
        border: 1px solid #ccc;
        padding: 5px;
        margin-bottom: 10px;
    }
    option {
        padding: 5px;
    }
</style>