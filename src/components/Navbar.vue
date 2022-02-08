<template>
    <nav class="navbar">
        <div class="navbar-brand"> 
              <a role="button" class="navbar-burger"  v-on:click="showNav = !showNav" v-bind:class="{ 'is-active' : showNav }" aria-label="menu" aria-expanded="false">
                  <span aria-hidden="true"></span>
                  <span aria-hidden="true"></span>
                  <span aria-hidden="true"></span>
              </a>
      </div>
      <div id="" class="navbar-menu" v-bind:class="{ 'is-active' : showNav}">
        <div class="navbar-end has-text-black">
            <a href="#" class="navbar-item">
                Visitor Info 
            </a>
            <a href="#" class="navbar-item">
              Events
            </a>
            <a href="#" class="navbar-item">
              Get Involved
            </a>
            <a class="navbar-item">
              <router-link to="about">
                  About
              </router-link>
          </a>
        </div>
      </div>
    </nav>
</template>

<script> 
    export default {
        name: 'Navbar', 
        data() {
            return {
                showNav: false,
                links: [],
            }
        }
    }
</script>
