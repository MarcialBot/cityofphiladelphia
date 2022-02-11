<template>
  <nav class="navbar has-text-light is-dark">
    <div
      role="button"
      class="navbar-burger"
      v-on:click="showNav = !showNav"
      v-bind:class="{ 'is-active': showNav }"
      aria-label="menu"
      aria-expanded="false"
    >
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
    </div>
    <div id="" class="navbar-menu" v-bind:class="{ 'is-active': showNav }">
      <div class="navbar-end has-text-dark is-size-6">
        <a
          v-for="link in links"
          v-bind:key="link.id"
          v-bind:href="link.url"
          class="navbar-item"
        >
          {{ link.title }}
        </a>
        <a class="navbar-item" href="/about">
          About - KM
        </a>
      </div>
    </div>
  </nav>
</template>

<script>
import axios from "axios";
export default {
  name: "Navbar",
  data() {
    return {
      showNav: false,
      links: [],
      loading: true,
      errored: false,
    };
  },
  created() {
    axios
      .get(
        "https://locations-staging-admin.phila.gov/love-park/wp-json/menus/v1/menus/main-menu"
      )
      .then((response) => {
        this.links = response.data.items;
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
};
</script>
