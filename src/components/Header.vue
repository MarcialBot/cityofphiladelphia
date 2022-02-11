<template>
  <section class="hero is-info is-small">
      <div class="hero-head">
        <div class="columns is-mobile is-centered">
          <div class="column is-three-fifths">
            <Navbar/>
          </div>
        </div>
      </div>
    <div class="hero-body">
        <div class="columns is-mobile is-centered">
          <div class="column is-three-fifths is-offset-2" style="width: 200px;">
            <router-link to="/">
             <figure class="image">
              <img class="banner-image" src="../assets/images/love-park-logo.png">
             </figure>
            </router-link> 
          </div>
          <div class="column is-three-fifths">
            <div class="container title-wrapper has-text-left">
               <h1 class="title is-3-mobile has-text-dark"> Spring Into LOVE</h1>
            </div>
          </div>
      </div>
    </div>
  </section>
</template>

<script>
  import Navbar from '@/components/Navbar'
  import axios from 'axios'

  export default {
    name: 'Header',
    components: {
        Navbar,
    },
    data() {
        return {
            post: [],
            loading: true,
            errored: false
            }
    },
    created() {
         axios.get('https://locations-staging-admin.phila.gov/love-park/wp-json/pages/v2/archive?id=4')
        .then(response => { 
            this.post = response.data 
        })
        .catch(error => {
            console.log(error)
            this.errored = true
        })
        .finally(() => this.loading = false)
    }
  }
</script>

<style scoped>
  .banner-image img {
    width: auto;
    height: auto;
    max-width: 100%;
    max-height: 100%; 
    padding-bottom: 25px;
  }
  .title-wrapper {
      height: 200px;
      position: relative;
      }
  .title {
    bottom: 25px;
    position: absolute;
      }
</style>
