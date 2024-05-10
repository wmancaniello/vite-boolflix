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


    // CHIAMATA IN PARALLELO
    getData() {
      console.log(this.store.query);
      const params = {
        api_key: this.store.apiKey,
        query: this.store.query,
      };

      // Richieste Axios
      const tvSeriesRequest = axios.get(
        "https://api.themoviedb.org/3/search/tv",
        {
          params,
        }
      );
      const movieRequest = axios.get(
        "https://api.themoviedb.org/3/search/movie",
        {
          params,
        }
      );

      axios.all([tvSeriesRequest, movieRequest]).then((resp) => {
        // FILM
        this.store.filmList = resp[1].data.results;
        console.log("Stampa Film:", this.store.filmList);

        // SERIE TV
        this.store.serieList = resp[0].data.results;
        console.log("Stampa Serie:", this.store.serieList);
      });
    },

    // CHIAMATE SEPARATE

    // searcher() {
    //   console.log(this.store.query);
    //   const paramsobj = {
    //     api_key: this.store.apiKey,
    //     query: this.store.query,
    //   };

    //   // Chiamata per le SERIE TV
    //   axios
    //     .get("https://api.themoviedb.org/3/search/tv", {
    //       params: paramsobj,
    //     })
    //     .then((resp) => {
    //       // Aggiorno la lista delle SERIE TV nello store con i risultati della ricerca (dovrei)
    //       this.store.serieList = resp.data.results;
    //       console.log("Stampa SerieTV", this.store.serieList);
    //     });

    //   // Chiamata per i FILM
    //   axios
    //     .get("https://api.themoviedb.org/3/search/movie", {
    //       params: paramsobj,
    //     })
    //     .then((resp) => {
    //       // Aggiorno la lista dei FILM nello store con i risultati della ricerca (dovrei)
    //       this.store.filmList = resp.data.results;
    //       console.log("Stampa FILM", this.store.filmList);
    //     });
    // },
  },
};
</script>

<template>
  <AppHeader @getData="getData" />
  <AppMain />
</template>

<style lang="scss"></style>
