<template>
  <footer>
  <div class="container is-justify-content-space-around">
    <div class="columns is-align-self-center	">
      <div class="column is-one-third">
        <ul>
        <b> Address </b>
            <li>
                {{ address.address_1 }}
                </li>
            <li>
            {{ address.city }}
            </li>
            <li>
              {{ address.state }}
            </li>
            <li>
                {{ address.zip }}
            </li>
            <li>
               <a v-bind:href="address.map_url">Map</a> 
            </li>
</ul>
      </div>
      <div class="is-divider-vertical"/>
      <div class="column is-one-third">
          <ul>
          <b>Hours</b>
                <li v-for="(value, name) in hours" v-bind:key="name.id">
                  <div v-if="name.toUpperCase() === date.toUpperCase() &&  value.exception == 1">
                      {{ value.exception_thursday }} {{ value.exception_wednesday }}
                  </div>
                  <div v-else-if="name.toUpperCase() === date.toUpperCase() && value.exception != 1">
                      {{ value.start_time }} - {{ value.end_time }}
                  </div>
                </li>
            </ul>
      </div>
      <div class="is-divider-vertical"/>
      <div class="column is-one-third">
           <ul>
                <b>
                    Contact
                </b>
                <li> 
                    {{ contact.email }} 
                </li>
                <li> 
                    {{ contact.phone}} 
                </li>
                <li> 
                   <a v-bind:href="contact.twitter"> <font-awesome-icon :icon="['fab', 'twitter']" /></a>
                   <a v-bind:href="contact.facebook"> <font-awesome-icon :icon="['fab', 'facebook']" /></a>
                   <a v-bind:href="contact.insta"> <font-awesome-icon :icon="['fab', 'instagram']" /></a>
                </li>
           </ul>

      </div>
      </div>
      </div>
  </footer>
</template>

<script>
  import axios  from 'axios'

  export default {
    name: 'Footer',
    methods: {
      getDate() {
          const today = new Date().toLocaleString('en-us', { weekday: 'long'});
          this.date = today.toString();
          console.log(today);
        },
    },
    data() {
      return {
          date: "",
          address: [],
          contact: [],
          hours: [],
          loading: true,
          errored: false
          }
    },
    created() {
         axios.get('https://locations-staging-admin.phila.gov/love-park/wp-json/locations/v1/connect')
        .then(response => { 
            console.log(response.data),
            this.address= response.data.address,
            this.contact= response.data.contact,
            this.hours= response.data.hours
        })
        .catch(error => {
            console.log(error)
            this.errored = true
        })
        .finally(() => this.loading = false);
        setInterval(this.getDate(),1000);
    },
  }
</script>
