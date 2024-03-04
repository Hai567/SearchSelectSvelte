<script>
    import SearchSelectSvelte from "$lib/SearchSelectSvelte.svelte";
    let list = ["a", "b", "c", "d"]
    let selectedValue
</script>

<div class="max-w-md mx-auto flex flex-wrap gap-10">
    <h1 class="font-bold text-3xl w-full">Search Select Svelte Demo</h1>
    <SearchSelectSvelte bind:selected={selectedValue}>
        {#each list as item}
            <li class="select-option" data-value={item}>{item}</li>
        {/each}
    </SearchSelectSvelte>
    
    <h3 class="text-xl w-full">Selected value: {selectedValue}</h3>
</div>