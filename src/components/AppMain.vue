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
    <div>
      <h2>Film:</h2>
      <div v-for="movie in store.filmList" :key="movie">
        <AppCards :cardObj="movie" />
      </div>
    </div>

    <!-- SerieTV -->
    <section>
        <h2>Serie TV:</h2>
        <div v-for="tv in store.serieList" :key="tv">
            <AppCards :cardObj="tv" />
        </div>
    </section>
  </main>
</template>

<style lang="scss" scoped>

h2 {
    color: red;
}

</style>
