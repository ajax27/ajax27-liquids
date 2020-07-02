<script>
  import Hero from '../components/Hero.svelte';
  import { link } from 'svelte-routing';
  // featured products
  import Featured from '../components/Products/Featured.svelte';
</script>
<svelte:head>
  <title>Ajax27 | Liquid Gold</title>
</svelte:head>
<Hero>
  <a href="/products" class="btn btn-primary btn-hero" use:link>shop now</a>
</Hero>
<Featured title="featured products" />
