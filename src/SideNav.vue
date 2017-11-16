<template>
  <div id="sideNav" class="">
    <ul class="nav">
      <li class="nav-item now-playing" :class="{ 'active' : active_link('now_playing')}">
        <a href="#" v-on:click="changeType('now_playing')">Now Playing</a>
      </li>
      <li class="nav-item popular" :class="{ 'active' : active_link('popular')}">
        <a href="#" v-on:click="changeType('popular')">Popular</a>
      </li>
      <li class="nav-item top-rated" :class="{ 'active' : active_link('top_rated')}">
        <a href="#" v-on:click="changeType('top_rated')">Top Rated</a>
      </li>
      <li class="nav-item upcoming" :class="{ 'active' : active_link('upcoming')}">
        <a href="#" v-on:click="changeType('upcoming')">Upcoming</a>
      </li>
    </ul>
  </div>
</template>

<script>
import SideNav from './SideNav.vue'
import Movies  from './Movies.vue'

export default {
  name: 'side-nav',
  data () {
    return {
      active_type: 'now_playing',
    }
  },
  created: function() {

  },
  components: {
    SideNav,
    Movies
  },
  computed: {

  }, 
  methods: {
    active_link(link) {
      return link == this.active_type
    },
    open_link (link) {
      window.open(link);
    },
    changeType(new_type) {
      // Call changeType(new_type) from App.vue
      this.active_type = new_type
      this.$emit('changeType',new_type)
    }
  }
}
</script>

<style lang="scss">
#sideNav {
  font-size: 1.8rem;
  font-size: 2.4rem;
  margin-left: 1rem;
  .active {
    a {
    color: #5755d9;
    }
  }
}
</style>
