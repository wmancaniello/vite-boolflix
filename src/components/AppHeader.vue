<script>
import { store } from "../store.js";
export default {
  data() {
    return {
      store,
    };
  },
  methods: {},
};
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
      <a class="navbar-brand" href="#">BOOLFLIX</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" href="#"
              >Home <span class="sr-only">(current)</span></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Film</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Serie TV</a>
          </li>
        </ul>
        <form class="form-inline my-2 my-lg-0 d-flex gap-2">
          <input
            class="form-control mr-sm-2"
            id="searcher"
            type="text"
            placeholder="Cerca"
            aria-label="Cerca"
            v-model="store.query"
          />
          <button
            class="btn btn-outline-success my-2 my-sm-0"
            type="submit"
            @click="$emit('getData')"
          >
            Cerca
          </button>
        </form>
      </div>
    </div>
  </nav>
</template>

<style lang="scss" scoped>
.nav-link {
  color: white;
}
</style>
