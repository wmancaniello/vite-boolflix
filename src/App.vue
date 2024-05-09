<script>
import { store } from "./store.js";
import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    searcher() {
      console.log(this.store.query);
      const paramsobj = {
        api_key: this.store.apiKey,
        query: this.store.query,
      };

      // Chiamata per le SERIE TV
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: paramsobj,
        })
        .then((resp) => {
          // Aggiorno la lista delle SERIE TV nello store con i risultati della ricerca (dovrei)
          this.store.serieList = resp.data.results;
          console.log("Stampa SerieTV", this.store.serieList);
        });

      // Chiamata per i FILM
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: paramsobj,
        })
        .then((resp) => {
          // Aggiorno la lista dei FILM nello store con i risultati della ricerca (dovrei)
          this.store.filmList = resp.data.results;
          console.log("Stampa FILM", this.store.filmList);
        });
    },
  },
};
</script>

<template>
  <AppHeader @searcher="searcher" />
</template>

<style lang="scss"></style>
