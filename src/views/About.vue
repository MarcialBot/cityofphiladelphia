<template>
  <div class="about">
    <Header></Header>
    <div class="container content-align is-overlay">
      <div class="columns is-mobile is-centered">
        <div class="column is-three-fifths">
          <h3 class="subtitle is-3">{{ info.title }}</h3>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-three-fifths is-fullwidth-mobile">
          <span v-html="info.content"></span>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-two-fifths">
          <figure class="image">
            <img src="../assets/images/parks-and-rec-logo.png" />
          </figure>
        </div>
      </div>
    </div>
    <div class="columns is-mobile is-centered has-background-link">
      <div class="column is-three-fifths">
        <Footer bgcolor="has-background-link" class="has-text-white"></Footer>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import axios from "axios";

export default {
  name: "About",
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      info: [],
      loading: true,
      errored: false,
    };
  },
  created() {
    axios
      .get(
        "https://locations-staging-admin.phila.gov/love-park/wp-json/pages/v2/archive?id=7"
      )
      .then((response) => {
        console.log(response.data);
        this.info = response.data;
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
.hero.is-info {
  background-color: #fffabc;
}
.has-background-link {
  background-color: #0e4d8f !important;
}
</style>
