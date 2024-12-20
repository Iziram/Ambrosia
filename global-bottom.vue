<!-- global-bottom.vue -->
<template>
  <footer class="absolute bottom-0 p-2">
    <span>Iziram</span>
    <span>Ambrosia</span>
    <span>{{ date }}</span>
    <span> <SlideCurrentNo /> / <SlidesTotal /> </span>
  </footer>
</template>

<script setup>
const date = new Date().toLocaleDateString("fr-FR", {
  day: "2-digit",
  month: "2-digit",
  year: "numeric",
});
</script>

<style scoped>
footer {
  display: flex;
  justify-content: space-evenly;
  width: 100%;
}
span {
  font-weight: lighter;
}
</style>
