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
    getOverview() {
      return this.cardObj.overview;
    },
    getLanguageFlag() {
      return "src/assets/img/flag/" + this.cardObj.original_language + ".png";
    },
  },
};
</script>

<template>
  <div class="container mt-3">
    <!-- Front Card -->
    <div class="card">
      <div class="front">
        <img class="flag" :src="getPoster" :alt="cardTitle" />
      </div>
      <!-- /Front Card -->

      <!-- Back Card -->
      <div class="back">
        <h4>Titolo: {{ cardTitle }}</h4>
        <p>Titolo Originale {{ cardOriginalName }}</p>
        <p>
          Lingua Originale: <img class="flag" :src="getLanguageFlag" alt="" />
        </p>
        <p>Voto: {{ cardObj.vote_average }}</p>
        <p>Overview: {{ getOverview }}</p>
      </div>
      <!-- /Back Card -->
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  height: 100%;
  width: 100%;
  border: 0;
  position: relative;
  transition: transform 1500ms;
  transform-style: preserve-3d;

  .back {
    height: 100%;
    width: 100%;
    border-radius: 2rem;
    position: absolute;
    text-align: center;
    background: linear-gradient(135deg, #1a1a1a, #333333);
    color: #ffffff;
    transform: rotateY(180deg);
    backface-visibility: hidden;

    .flag {
      max-width: 36px;
    }
  }

  .front {
    img {
      border-radius: 2rem;
    }
  }
}

.container:hover > .card {
  cursor: pointer;
  transform: rotateY(180deg);
}
</style>
