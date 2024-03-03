<script>
    import SeachSelectSvelte from "$lib/SeachSelectSvelte.svelte";
    let list = ["a", "b", "c", "d"]
    let selectedValue
</script>

<div class=" max-w-md mx-auto flex flex-wrap gap-10">
    <h1 class="font-bold text-3xl w-full">Search Select Svelte Demo</h1>
    <SeachSelectSvelte bind:selected={selectedValue}>
        {#each list as item}
            <li class="select-option" data-value={item}>{item}</li>
        {/each}
    </SeachSelectSvelte>
    
    <h3 class="text-xl w-full">Selected value: {selectedValue}</h3>
</div>