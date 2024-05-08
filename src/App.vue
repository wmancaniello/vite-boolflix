<script>
import { store } from "./store.js";
import axios from "axios";

import AppHeader from ".components/AppHeader.vue";

export default {
  components: {
    AppHeader,
  },
  data() {
    return {
      store,
    };
  },
  methods: {},
};
</script>

<template>
  <Appheader />
</template>

<style lang="scss">

</style>
