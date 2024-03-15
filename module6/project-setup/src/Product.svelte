<script>
  import { createEventDispatcher } from "svelte";
  export let title;
  export let price;
  export let bestseller = false;

  const dispatch = createEventDispatcher();

  const addToCart = () => {
    dispatch("add-to-cart", { id: 1 });
  };
  const deleteFromCart = () => {
    dispatch("delete", { id: 1 });
  };
</script>

<article>
  <h1>{title}</h1>
  <h1>{price}</h1>
  {#if bestseller}
    <h3>**BESTSELLER**</h3>
  {/if}
  <button on:click={addToCart}>Add to cart</button>
  <button on:click={deleteFromCart}>delete</button>
</article>
