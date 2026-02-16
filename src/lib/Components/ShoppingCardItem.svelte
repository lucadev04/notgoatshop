<script>
  let { name, image } = $props();
</script>

<style>
    @import './style.css';
</style>

<div class="item">
    <h1 class="title">{name}</h1>
    <div class="image-container">
        <img src= {image} alt="irgendein dummes Bild von Ziegenhainy" class="image"/>
    </div>
</div>