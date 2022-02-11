<template>
  <div class="home">
    <Header></Header>
    <div class="container content-align is-overlay">
      <div class="columns is-mobile is-centered">
        <div class="column is-three-fifths is-fullwidth-mobile">
          <figure class="image is-fullwidth">
            <img src="../assets/images/love-park-hero.jpeg" />
          </figure>
        </div>
      </div>
    </div>
    <div class="columns is-mobile is-centered">
      <div class="column is-three-fifths">
        <Footer
          class="is-size-9 has-text-black"
          bgcolor="has-background-link"
        ></Footer>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";

export default {
  name: "About",
  components: {
    Header,
    Footer,
  },
};
</script>

<style scoped>
.hero-body {
  background-color: black;
}
.hero.is-info .title {
  color: black !important;
}
.navbar-end {
  color: black;
}
.hero.is-info {
  background-color: #b3e8f9;
  color: #fff;
}
.top-padding {
  padding-top: 20px;
}
</style>
