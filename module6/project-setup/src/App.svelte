<script>
  import Product from "./Product.svelte";
  import Modal from "./Modal.svelte";
  export let name;
  let products = [
    {
      id: "0",
      title: "book",
      price: 10.99,
    },
    {
      id: "1",
      title: "pen",
      price: 1.99,
    },
  ];

  let openModal = false;
  let closable = false;

  const modalHandler = () => (openModal = !openModal);
</script>

<h1>Hello {name}!</h1>
{#each products as product (product.id)}
  <!-- content here -->
  <Product
    {...product}
    on:add-to-cart={() => alert("add to cart")}
    on:delete={() => alert("delete")}
  />
{/each}
<button on:click={modalHandler}>Open Modal</button>

{#if openModal}
  <Modal on:closeModal={modalHandler} let:didAgreed={closable}>
    <h1 slot="header">Hello</h1>
    <p>This works!!!!!</p>
    <button on:click={modalHandler} slot="footer" disabled={!closable}
      >Confirm</button
    >
  </Modal>
{/if}

<style>
  h1 {
    color: purple;
  }
</style>
