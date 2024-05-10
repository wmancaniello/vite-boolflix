<script>
export default {
  props: {
    cardObj: Object,
  },
  computed: {
    cardTitle() {
      return !!this.cardObj.title ? this.cardObj.title : this.cardObj.name;
    },
    cardOriginalName() {
      return !!this.cardObj.original_title
        ? this.cardObj.original_title
        : this.cardObj.original_name;
    },
    getPoster() {
      return !!this.cardObj.poster_path
        ? "https://image.tmdb.org/t/p/w300" + this.cardObj.poster_path
        : "src/assets/img/Icona-Cristo.jpg";
    },
  },
};
</script>

<template>
  <div class="container mt-3 bg-secondary">
    <!-- Front Card -->
    <div>
      <img :src="getPoster" :alt="cardTitle" />
    </div>
    <!-- /Front Card -->

    <!-- Back Card -->
    <div>
      <h4>Titolo: {{ cardTitle }}</h4>
      <p>Titolo Originale {{ cardOriginalName }}</p>
      <p>Lingua Originale: {{ cardObj.original_language }}</p>
      <p>Voto: {{ cardObj.vote_average }}</p>
    </div>
    <!-- /Back Card -->
  </div>
</template>

<style lang="scss" scoped></style>
