<template>
    <div class="about">
        <Header></Header>
        <div class="container content-align is-overlay">
            <div class="columns">
                <div class="column">
                    <h3 class="subtitle is-3">{{ info.title  }}</h3>
                </div>
            </div>
            <div class="columns">
                <div class="column has-text-justified"> <span v-html="info.content"></span>
                </div>
            </div>
            <div class="columns">
                <div class="column is-one-quarter is-offset-4">
                    <figure class="image">
                        <img src="../assets/images/parks-and-rec-logo.png">
                    </figure>
                </div>
            </div>
        </div>
        <div class="has-background-link">
            <div class="container">
                <Footer bgcolor="has-background-link" class="has-text-white"></Footer>
            </div>
        </div>
    </div>
</template>

<script>
import Header from "@/components/Header.vue"
import Footer from "@/components/Footer.vue"
import axios from 'axios'

export default {
  name: "About",
  components: {
    Header, 
    Footer
  },
  data() {
      return {
          info: [],
          loading: true,
          errored: false
      }
  },
  created() {
    axios.get('https://locations-staging-admin.phila.gov/love-park/wp-json/pages/v2/archive?id=7')
         .then(response => { 
           console.log(response.data)
            this.info = response.data
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
    .hero.is-info {
        background-color: #FFFABC;
        } 
    .has-background-link {
        background-color: #0E4D8F !important;
        }
</style>
