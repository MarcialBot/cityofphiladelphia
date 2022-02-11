<template>
  <footer>
    <div class="columns is-centered">
      <div class="column is-narrow">
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
      <div class="is-divider-vertical" />
      <div class="column is-3">
        <ul>
          <b>Hours</b>
          <li v-for="(value, name) in hours" v-bind:key="name.id">
            <div
              v-if="
                name.toUpperCase() === date.toUpperCase() &&
                  value.exception == 1
              "
            >
              {{ value.exception_thursday }} {{ value.exception_wednesday }}
            </div>
            <div
              v-else-if="
                name.toUpperCase() === date.toUpperCase() &&
                  value.exception != 1
              "
            >
              {{ value.start_time }} - {{ value.end_time }}
            </div>
          </li>
          <li>
            <a v-on:click="isHidden = !isHidden">See all hours</a>
          </li>
        </ul>
        <div
          class="notification is-full is-full-mobile has-background-dark has-text-white-ter"
          v-if="!isHidden"
        >
          <ul>
            <li v-for="(value, name) in hours" v-bind:key="name.id">
              {{ capitalize(name) }}: {{ value.start_time }} -
              {{ value.end_time }}
            </li>
          </ul>
        </div>
      </div>
      <div class="is-divider-vertical" />
      <div class="column is-narrow">
        <ul>
          <b>
            Contact
          </b>
          <li>
            {{ contact.email }}
          </li>
          <li>
            {{ contact.phone }}
          </li>
          <li>
            <a v-bind:href="contact.twitter"
              ><font-awesome-icon :icon="['fab', 'twitter']"
            /></a>
            <a v-bind:href="contact.facebook"
              ><font-awesome-icon :icon="['fab', 'facebook']"
            /></a>
            <a v-bind:href="contact.insta">
              <font-awesome-icon :icon="['fab', 'instagram']"
            /></a>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script>
import axios from "axios";

export default {
  name: "Footer",
  methods: {
    getDate() {
      const today = new Date().toLocaleString("en-us", { weekday: "long" });
      this.date = today.toString();
      console.log(today);
    },
    capitalize(value) {
      if (!value) return "";
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
  },
  data() {
    return {
      date: "",
      address: [],
      contact: [],
      hours: [],
      loading: true,
      errored: false,
      isHidden: true,
    };
  },
  created() {
    axios
      .get(
        "https://locations-staging-admin.phila.gov/love-park/wp-json/locations/v1/connect"
      )
      .then((response) => {
        console.log(response.data),
          (this.address = response.data.address),
          (this.contact = response.data.contact),
          (this.hours = response.data.hours);
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
    setInterval(this.getDate(), 1000);
  },
};
</script>
