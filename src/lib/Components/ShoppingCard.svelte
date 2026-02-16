<script lang="ts">
  import ShoppingCardItem from './ShoppingCardItem.svelte';
  import { onMount } from 'svelte';

  let { visibility } = $props();

  interface Item {
    name: string;
    image: string;
  }

  let items: Item[] = $state([]);

  onMount(() => {
    items = getItems();
  });

  function getItems(): Item[] {
    if (typeof window !== 'undefined') {
      let items = localStorage.getItem("items");
      if (items === null) {
        localStorage.setItem("items", "[]");
        return [];
      }
      return JSON.parse(items);
    }
    return [];
  }
</script>

<div class="Card">
  <div class={visibility}>
    <h1>Warenkorb</h1>
    {#each items as item (item.name)}
        <ShoppingCardItem name={item.name} image={item.image} />
    {/each}
   </div>
</div>

<style>
  @import './styleCard.css';
</style>
