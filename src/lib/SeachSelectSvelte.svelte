<script>
    import "../app.css"
    export let selected, inputPlaceholder, boardCssClass
    import { onMount } from "svelte";
    let isDropdownOpen = false

    let mediaList, query
    function filterQuery() {
        let userFilter = query.toUpperCase();
        let mediaItems = mediaList.querySelectorAll("li.select-option")
        mediaItems.forEach(mediaPlatformEle => {
            let mediaValue = mediaPlatformEle.getAttribute("data-value").toUpperCase()
            if (mediaValue.includes(userFilter)){
                mediaPlatformEle.style.display = ""
            } else {
                mediaPlatformEle.style.display = "none"
            }
        });
    }
    onMount(() => {
        let mediaItems = mediaList.querySelectorAll("li.select-option")
        mediaItems.forEach(mediaLiEle => {
            mediaLiEle.addEventListener("click", () => {
                let selectedValue = mediaLiEle.getAttribute("data-value")
                query = selectedValue
                selected = selectedValue
                isDropdownOpen = false
            })
        });
    })
    function toggleDropdown() {
        isDropdownOpen = !isDropdownOpen
    }
</script>
<div id="select_search_svelte" class="w-full">
    <input type="text" tabindex="0" class="w-full px-2" placeholder={inputPlaceholder || "Search here"} bind:value={query} on:keyup={filterQuery} on:click={toggleDropdown}>
    <!-- svelte-ignore a11y-no-noninteractive-tabindex -->
    <div class="w-full relative">
        <ul id="" tabindex="0" class:hidden={!isDropdownOpen} class="block absolute p-2 rounded-lg max-h-[15em] w-full z-[1] bg-white {boardCssClass}" bind:this={mediaList}>
            <slot></slot>
        </ul>
    </div>
    <input type="text" class="hidden selected" bind:value={selected}>
</div>
