<script>
	import Product from "./product.svelte";
	import Button from "./button.svelte";
	import Cart from "./cart.svelte";
	
	let title = '';
	let price = 0;
	let desc = '';

	let products = [];
	let cartItems = [];

	function setTitle(event){
		title = event.target.value;
	}
	function createProduct(){
		const newProduct = {
			title: title,
			price: price,
			desc: desc
		};
		products = products.concat(newProduct);
	}
	function addToCart(event){
		const selectedTitle = event.detail;
		cartItems = cartItems.concat(
			{...products.find(prod => prod.title === selectedTitle)
		});
		console.log(cartItems);
	}
</script>

<style>
	section{
		width: 30rem;
		margin: auto;
	}
	label, input, textarea{
		width: 100%;
	}
</style>

<section>
	<Cart items={cartItems}/>
</section>

<hr>

<section>
	<div>
		<label for="title">Title</label>
		<input type="text" id="title" value="{title}" on:input="{setTitle}" />
	</div>
	<div>
		<label for="price">Price</label>
		<input type="number" id="price" bind:value={price} />
	</div>
	<div>
		<label for="desc">Description</label>
		<textarea rows="3" id="desc" bind:value={desc}></textarea>
	</div>

	<Button on:click={createProduct}>Create Product</Button>

</section>

<section>
	{#if products.length === 0}
		<p>No products were added yet.</p>
	{:else}
		{#each products as product}
			<Product 
				prodTitle={product.title} 
				prodPrice={product.price} 
				prodDesc={product.desc}
				on:addcart={addToCart} />
		{/each}
	{/if}
</section>
