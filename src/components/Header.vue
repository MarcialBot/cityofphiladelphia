<template>
  <section class="hero is-info is-small">
  <div class="hero-body">
    <div class="hero-head">
        <Navbar></Navbar>  
    </div>
<div class="columns has-text-left">
          <div class="column is-narrow">
              <router-link to="/">
                <a>
                  <img class="banner-image" src="../assets/images/love-park-logo.png">
                </a>
              </router-link> 
          </div>
          <div class="column">
            <h1> Lorem Ipsum </h1>
          </div>
      </div>
    </div>
  </section>
</template>

<script>
  import Navbar from '@/components/Navbar'

  export default {
    name: 'Header',
    components: {
        Navbar,
    }
  }
</script>

<style scoped>
  .banner-image {
    height: 220px;
    padding-bottom: 25px;
  }
</style>
