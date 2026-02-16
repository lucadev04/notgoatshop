<script lang="ts">
  import { ShoppingCart } from '@lucide/svelte';
  import ShoppingItem from '$lib/Components/ShoppingItem.svelte';
  import ShoppingCard from '$lib/Components/ShoppingCard.svelte';

  interface Item {
    name: string;
    image: string;
  }

  let items: Item[] = [];
  let visibility = $state("hidden")

  for (let i = 0; i < 1000; i++) {
    items.push({ name: `Item ${i + 1}`, image: randomImage() });
  }

  function randomImage() {
    let randomInt = Math.floor(Math.random() * 4);
    let image = "";

    switch (randomInt) {
      case 0:
        image = "https://media.discordapp.net/attachments/1463870568418770990/1472869646985072680/image.png?ex=69942440&is=6992d2c0&hm=d46658bdb28864a966c5f92fcee646f75ebac0236d37df965b9346b7a401c808&=&format=webp&quality=lossless&width=404&height=415";
        break;
      case 1:
        image = "https://media.discordapp.net/attachments/1463870568418770990/1472857528952950794/image.png?ex=699418f7&is=6992c777&hm=5b9ff4c0555f7a8c56a73fcc4a3262db850470bc14270a323c873874922ac4e2&=&format=webp&quality=lossless&width=675&height=488";
        break;
      case 2:
        image = "https://cdn.discordapp.com/attachments/1463870568418770990/1472880738348044358/image.png?ex=69942e94&is=6992dd14&hm=a8108fcc6421bf68e3d5251cbf99d82d72e57e108636d7200cf95c4eba40d4bf&";
        break;
      case 3:
        image = "https://cdn.discordapp.com/attachments/1463870568418770990/1472881022608740467/image.png?ex=69942ed8&is=6992dd58&hm=08aa6d2e69a29636fd1c370ca4c24e40c333882a093a6396f6c516f7d5319f06&";
        break;

    }

    return image;
  }

  function changeVisibility() {
    if (visibility == "visible") {
        visibility = "hidden"
    } else {
        visibility = "visible"
    }
  }
</script>

<div class="header">
  <h1>Not goat shop</h1>
  <button class="flex items-end hover:bg-sky-700 hover:rounded-xl hover:border-15" onclick={changeVisibility}>
    <ShoppingCart />
  </button>
</div>
<ShoppingCard visibility={visibility} />
<div class="grid grid-cols-3 gap-y-4">
  {#each items as item}
    <ShoppingItem name={item.name} image={item.image} />
  {/each}
</div>
