<script>
    import Button from './button.svelte';
    import { createEventDispatcher } from 'svelte';

    export let prodTitle;
    export let prodPrice;
    export let prodDesc;

    const dispatch = createEventDispatcher();

    function addToCart(){
        dispatch('addcart', prodTitle);
    }
</script>

<style>
    div{
        margin: 1rem;
        box-shadow: 0 2px 8px rgba(0,0,0,0.25);
        padding: 1rem;
        border-radius:5px;
        background: whitesmoke;
    }
    h1{
        font-size:1.25rem;
        margin: 0.25rem 0;
    }
    h2{
        font-size: 1rem;
        margin: 0.25rem 0;
        color:rgb(79, 79, 79);
    }
    p{
        margin: 0.25 0;
    }
</style>

<div>
    <h1>{prodTitle}</h1>
    <h2>{prodPrice}</h2>
    <p>{prodDesc}</p>
    <Button on:click={addToCart}>Add to Cart</Button>
</div>