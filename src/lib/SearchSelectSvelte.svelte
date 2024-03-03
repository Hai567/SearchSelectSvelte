<script>
    import "../app.css"
    export let selected, inputPlaceholder, dropdownCssClass, dropdownStyle
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

<svelte:head>
    <style>
        .max-w-md{
            max-width: 28rem
        }
        .mx-auto {
            margin-left: auto;
            margin-right: auto;
        }
        .flex {
            display: flex;
        }
        .flex-wrap {
            flex-wrap: wrap;
        }
        .gap-10 {
            gap: 2.5rem
        }
        .font-bold {
            font-weight: 700;
        }
        .w-full {
            width: 100%;
        }
        .text-3xl {
            font-size: 1.875rem;
            line-height: 2.25rem;
        }
        .text-xl {
            font-size: 1.25rem;
            line-height: 1.75rem;
        }
        .px-2 {
            padding-left: 0.5rem;
            padding-right: 0.5rem;
        }
        .relative {
            position: relative;
        }
        .hidden {
            display: none;
        }
        .block {
            display: block;
        }
        .absolute {
            position: absolute;
        }
        .rounded-lg {
            border-radius: 0.5rem;
        }
        .max-h-\[15em\] {
            max-height: 15em;
        }
        .z-\[1\] {
            z-index: 1;
        }
        .bg-white {
            --tw-bg-opacity: 1;
            background-color: rgb(255 255 255 / var(--tw-bg-opacity));
        }
        .input-bordered {
            border: 1px solid black;
            border-radius: 8px;
            padding: 0.5rem;
        }
    </style>
</svelte:head>

<div id="select_search_svelte" class="w-full">
    <input type="text" tabindex="0" class="w-full input-bordered" placeholder={inputPlaceholder || "Search here"} bind:value={query} on:keyup={filterQuery} on:click={toggleDropdown}>
    <!-- svelte-ignore a11y-no-noninteractive-tabindex -->
    <div class="w-full relative">
        <ul id="" tabindex="0" style={dropdownStyle ||''} class:hidden={!isDropdownOpen} class="block absolute p-2 rounded-lg max-h-[15em] w-full z-[1] bg-white {dropdownCssClass, dropdownStyle}" bind:this={mediaList}>
            <slot></slot>
        </ul>
    </div>
    <input type="text" class="hidden selected" bind:value={selected}>
</div>
