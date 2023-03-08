<!-- Dropdown.svelte -->
<script>
  export let options = [];
  export let selectedOption = null;
  let filteredOptions = [...options];
  let isDropdownOpen = false;

  function toggleDropdown() {
    isDropdownOpen = !isDropdownOpen;
  }

  function handleSelect(option) {
    selectedOption = option;
    toggleDropdown();
  }

  function filterOptions(event) {
    let searchQuery = event.target.value.toLowerCase();

    let finalOptions = [];

    options.forEach((parentOption) => {
      let childOptions = [];
      parentOption.options.forEach(childOption => {
        if (childOption.label.toLowerCase().includes(searchQuery)) {
          childOptions.push(childOption);
        }
      })

      if (childOptions.length > 0) {
        finalOptions.push({
          groupName: parentOption.groupName,
          options: childOptions
        })
      }
    })

    filteredOptions = finalOptions;
  }

</script>

<div class="dropdown">
  <div class="dropdown-toggle" on:click={toggleDropdown}>
    {selectedOption ? selectedOption.label : 'Select an option...'}
  </div>
  {#if isDropdownOpen}
    <div class="dropdown-menu">
      <input
        type="text"
        placeholder="Search..."
        on:input={filterOptions}
      />
      {#each filteredOptions as option}
          <div class="label">
            {option.groupName}
          </div>
          {#each option.options as childOption}
            <div class="dropdown-item" on:click={() => handleSelect(childOption)}>
              {childOption.label}
            </div>
          {/each}
      {/each}
    </div>
  {/if}
</div>

<style>
  .label{
    padding-left: 5px;
    font-weight: bold;
  }
  input{
    margin: 5px;
    width: 525px;
    padding: 0px;
  }
  input[type=text]{
    padding: 5px;
  }
  .dropdown {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 550px;
    position: relative;
  }

  .dropdown-toggle {
    cursor: pointer;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #fff;
  }

  .dropdown-menu {
    position: absolute;
    top: 100%;
    left: 0;
    z-index: 1;
    width: 100%;
    max-height: 200px;
    overflow-y: auto;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #fff;
  }

  .dropdown-item {
    cursor: pointer;
    padding: 5px 0px 5px 15px;
  }

  .dropdown-item:last-child {
    border-bottom: none;
  }

  .dropdown-item:hover {
    background-color: #2094fc;
    color: #fff;
  }
</style>
