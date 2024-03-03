
# Search Select Svelte (SSS)

A light weight, easy to use select Svelte component with lots of handy integrated features



## Authors

[@Daniel Ho](https://github.com/Hai567)


## Demo

A demo app of this component can be seen [here](https://svelte.dev/repl/96062f3357ea4f61b6dfffe8fb90b20a?version=4.2.12).


## Features

- Allows more than just text to be displayed in select (eg: emoji, icon, etc).
- Allows searching for the corresponding value.
- Customable UI (using global classes, lib, etc).


## Installation

Install SearchSelectSvelte with npm

```bash
npm i @canadies/searchselectsvelte
```
    
## Usage/Examples

```svelte
<script>
	import {SearchSelectSvelte} from "@canadies/searchselectsvelte@1.0.6"
    let list = ["a", "b", "c", "d"]
    let selectedValue
</script>

<svelte:head>
	<script src="https://cdn.tailwindcss.com"></script>
</svelte:head>

<div class=" max-w-md mx-auto flex flex-wrap gap-10">
    <h1 class="font-bold text-3xl w-full">Search Select Svelte Demo</h1>
    <SearchSelectSvelte bind:selected={selectedValue}>
        {#each list as item}
            <li class="select-option" data-value={item}>{item}</li>
        {/each}
    </SearchSelectSvelte>
    
    <h3 class="text-xl w-full">Selected value: {selectedValue}</h3>
</div>
```


## Properties


| Properties | Type     | Description                       | 
| :-------- | :------- | :-------------------------------- |
| `selected`      | `string` | **Required**. Used to bind the selected value |
| `inputPlaceholder`      | `string` | **Optional**. Placeholder of the select (default: 'Search here') |
| `dropdownCssClass`      | `string` | **Optional**. Style the select dropdown using css class (global css, tailwind, etc) as you wish |
| `dropdownStyle`      | `string` | **Optional**. Style the select dropdown using css style as you wish |



## Support

For further support, feel free to email danielho567@gmail.com.

## Issues
If you find any bugs, be my guest to create new issues ♥️♥️

