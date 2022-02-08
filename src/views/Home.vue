<template>
    <div class="home">
        <Header></Header>
        <div class="container content-align is-overlay">
            <figure class="image">
              <img src="../assets/images/love-park-hero.jpeg">
            </figure>
                <Footer bgcolor="has-background-link" textcolor="has-text-black"></Footer>
        </div>
    </div>
</template>

<script>
  import Header from '@/components/Header.vue'
  import Footer from '@/components/Footer.vue'

  export default {
    name: 'About',
    components: {
        Header,
        Footer
    }
  }
</script>

<style scoped>
  .hero.is-info .title {
      color: black;
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
