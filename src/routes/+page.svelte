<script>
    let quantity = 0;
    function addToCart() {
        inventory = [...inventory, quantity]
        quantity = ++quantity
        user.name = 'Lee'
    };
    let inventory = [1,2,3];
    let user = { name: 'Steph' };
    $: remaining = 10 - quantity;
    let price = 5;
    $: totalcost =  quantity * price;

    function handleClick(string) {
        alert(string)
    }

    let searchValue = '';
    function setSearchValue() {
        searchValue = document.getElementById("myText").value
    }

    let checked = false


    let product = {
        name: 't-shirt',
        quantityt: 0
    };
    function increment() {
        product.quantityt += 1;
    }

    let products = [
        {name: 't-shirt', quantities: 10},
        {name: 'mug', quantities: 30},
        {name: 'sticker', quantities: 8},
        {name: 'sweatshirt', quantities: 12},
    ];
    function addProduct() {
        let cup = {name: 'cup', quantities: 4};
        products = [cup, ...products];
    };
</script> 

<h1>Your shopping cart has {quantity} items.</h1>
<button on:click={addToCart}>Add to Cart</button>
<h2>{inventory}</h2>
<h3>{user.name}</h3>
<div>Remaining Inventory: {remaining}</div>
<div>Item Price: {price}</div>
<div>Total Cost: {totalcost}</div>
<div on:click={() => {handleClick('Clicked on green box')}} style="background-color: chartreuse;">Green Box</div>


<h3>Search: {searchValue}</h3>
<input bind:value={searchValue} type="text" id="myText">

<h3>Checked: {checked}</h3>
<input type="checkbox" bind:checked={checked}>

{#if product.quantityt > 10}
    <div style="background: lightgreen; padding: 4px;">This product is in stock</div>
    {:else if product.quantityt == 0}
    <div style="background: lightcoral; padding: 4px">Out of stock</div>
    {:else}
    <div style="background: lemonchiffon; padding: 4px;">Only a few items left</div>
    {/if}
<h1>Current {product.name} quantity: {product.quantityt}</h1>
<button on:click={increment}>Increment</button>



<button on:click={addProduct}>Add product</button>
{#each products as p, i(p.name)}
    <h3>{p.name}</h3>
    <input type="checkbox"/>
    <div>{i}</div>
{/each}