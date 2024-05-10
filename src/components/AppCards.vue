<script>
export default {
  props: {
    cardObj: Object,
  },
  computed: {
    cardTitle() {
      return this.cardObj.title ? this.cardObj.title : this.cardObj.name;
    },
    cardOrName() {
        return this.cardObj.original_title ? this.cardObj.original_title : this.cardObj.original_name;
    }
  },
};
</script>

<template>
  <div>
    <h4>Titolo: {{ cardTitle }}</h4>
    <p>Titolo Originale {{ cardOrName }}</p>
    <p>Lingua Originale: {{ cardObj.original_language }}</p>
    <p>Voto: {{ cardObj.vote_average }}</p>
  </div>
</template>

<style lang="scss" scoped></style>
