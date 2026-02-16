<script>
  let { name, image } = $props();

  function getItems() {
    let items = localStorage.getItem("items");
    if (items === null) {
      localStorage.setItem("items", "[]");
      return [];
    }
    return JSON.parse(items);
  }

  function addItem() {
    let items = getItems();
    items.push({ name: name, image: image });
    localStorage.setItem("items", JSON.stringify(items));
  }
</script>

<style>
    @import './style.css';
</style>

<div class="item">
    <h1 class="title">{name}</h1>
    <div class="image-container">
        <img src= {image} alt="irgendein dummes Bild von Ziegenhainy" class="image"/>
    </div>
    <div class="button-container">
        <button class="card-button" onclick={addItem}>add to card</button>
    </div>
</div>