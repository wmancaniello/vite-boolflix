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
  <main>
    <!-- Film -->
    <h1>Film:</h1>
    <div class="row row-cols-4">
      <div v-for="movie in store.filmList" :key="movie" class="col">
        <AppCards :cardObj="movie" />
      </div>
    </div>

    <!-- SerieTV -->
    <h1>Serie TV:</h1>
    <div class="row row-cols-4">
      <div v-for="tv in store.serieList" :key="tv" class="col">
        <AppCards :cardObj="tv" />
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
h1 {
  color: red;
}
</style>
