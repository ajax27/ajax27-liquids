<script>
  export let id;
  export let location;
  import { addToCart } from '../stores/cart';
  import products from '../stores/products';
  import Loading from '../components/Loading.svelte';
  import { link } from 'svelte-routing';
  import globalStore from '../stores/globalStore';
  $: product = $products.find(item => item.id === parseInt(id));
</script>
<svelte:head>
  <title>Liquid Gold | {!product ? 'Single Product' : product.title}</title>
</svelte:head>
{#if !product}
  <Loading />
{:else}
  <section class="single-product">
    <a href="/products" class="btn btn-primary" use:link>back to products</a>
    <!-- single product container -->
    <div class="single-product-container">
      <article class="single-product-image">
        <img src={product.image} alt={product.title} />
      </article>
      <article>
        <h1>{product.title}</h1>
        <h2>£{product.price}</h2>
        <p>{product.description}</p>
        <button class="btn btn-primary btn-block" on:click={() => { 
          addToCart(parseInt(id), product);
          globalStore.toggleItem('cart', true);
        }}>
          add to cart
        </button>
      </article>
      <a href="/" class="btn btn-primary" use:link>back to home page</a>
    </div>
  </section>
{/if}
