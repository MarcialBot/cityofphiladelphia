<template>
  <div>
    <div class="columns">
      <div class="column">
        <ul>
            <li>
                Address
            </li>
            <li>
                {{ info.address_1 }} 
            </li>
            <li>
            </li>
        </ul>
      </div>
      <div class="column">
        Hours
      </div>
      <div class="column">
        Contact
      </div>
      </div>
  </div>
</template>

<script>
  import axios  from 'axios'

  export default {
    name: 'Footer',
    methods: {},
    data() {
      return {
          info: null
          }
    },
    created() {
    },
    mounted() {
        axios.get('https://locations-staging-admin.phila.gov/love-park/wp-json/locations/v1/connect')
        .then(response => (this.info = response.data.address))
    },
    }
</script>
