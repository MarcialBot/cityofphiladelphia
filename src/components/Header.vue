<template>
  <section class="hero is-info is-small">
    <div class="hero-head">
      <div class="columns is-mobile is-centered">
        <div class="column is-three-fifths">
          <Navbar />
        </div>
      </div>
    </div>
    <div class="hero-body">
      <div class="columns is-mobile is-centered">
        <div class="column is-8 is-offset-1">
          <div class="tile is-ancestor">
            <div class="tile is-2">
              <router-link to="/">
                <figure class="image">
                  <img
                    class="banner-image is-1by1"
                    src="../assets/images/love-park-logo.png"
                  />
                </figure>
              </router-link>
            </div>
            <div class="tile is-narrow">
              <h1 class="title has-text-dark">Spring Into LOVE</h1>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Navbar from "@/components/Navbar";
import axios from "axios";

export default {
  name: "Header",
  components: {
    Navbar,
  },
  data() {
    return {
      post: [],
      loading: true,
      errored: false,
    };
  },
  created() {
    axios
      .get(
        "https://locations-staging-admin.phila.gov/love-park/wp-json/pages/v2/archive?id=4"
      )
      .then((response) => {
        this.post = response.data;
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
};
</script>

<style scoped>
.banner-image {
  width: auto;
  height: auto;
  max-height: 200px;
}
.title {
  margin-top: auto;
}
</style>
