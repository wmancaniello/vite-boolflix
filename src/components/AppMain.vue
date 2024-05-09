<script>
import { store } from "../store";
import AppCards from "./AppCards.vue";
export default {
  components: {
    AppCards,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="container">
    <h1 class="text-center">Risultati:</h1>
    <div class="row row-cols-4">
      <div class="col">
        <AppCards />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
