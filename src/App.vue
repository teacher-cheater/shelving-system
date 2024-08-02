<template>
  <ProductListing />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ProductListing from "./components/ProductListing.vue";

export default defineComponent({
  name: "App",
  components: {
    ProductListing,
  },
});
</script>

<style>
#app {
  font-family: "SF Pro Display", sans-serif;
  [class*="__container"] {
    max-width: 1520px;
    margin: 0px auto;
  }
}
</style>
