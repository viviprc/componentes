<template>
  <div class="contenedor">
    <img class="imagen-personaje" :src="src" alt />
    <h3>{{characterName}}</h3>
  </div>
</template>

<script>
export default {
  name: "Character",
  props: {
    src: String,
    characterName: String,
  },
};
</script>

<style>
</style>